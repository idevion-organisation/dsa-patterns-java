# Pattern 11: Variable Size Sliding Window

Variable Size Sliding Window is an array pattern used when the window size is not fixed.

The window can grow or shrink depending on a condition.

It is mainly used for problems like:

```txt
longest subarray
smallest subarray
maximum length
minimum length
at most k
sum less than or equal to target
sum greater than or equal to target
```

---

## What Is Variable Size Sliding Window?

In Fixed Size Sliding Window, the window size is already given.

Example:

```txt
subarray of size k
```

But in Variable Size Sliding Window, the size is not fixed.

Example:

```txt
Find the longest subarray whose sum is less than or equal to target.
```

Here, the window can be:

```txt
size 1
size 2
size 3
size 4
...
```

depending on the condition.

---

## Simple Meaning

```txt
Expand the window from right side
Check if condition is valid
If condition becomes invalid, shrink from left side
Update answer whenever window is valid
```

---

## Fixed Size vs Variable Size Sliding Window

| Point | Fixed Size Window | Variable Size Window |
|---|---|---|
| Window size | Given as `k` | Changes based on condition |
| Common question | Subarray of size `k` | Longest / smallest subarray |
| Movement | Add one, remove one | Expand and shrink as needed |
| Example | Max sum of size `k` | Longest sum <= target |

---

## Important Word: Subarray

Sliding Window works on subarrays.

A subarray means a continuous part of an array.

Example:

```txt
nums = [1, 2, 3, 4]
```

Valid subarrays:

```txt
[1, 2]
[2, 3]
[2, 3, 4]
```

Invalid:

```txt
[1, 3]
```

Because elements are skipped.

---

## Pattern Signal

Think of Variable Size Sliding Window when the question says:

```txt
longest subarray
smallest subarray
minimum length
maximum length
at most k
less than or equal to k
greater than or equal to k
continuous subarray
condition-based window
```

Most common signals:

```txt
Longest subarray with condition
Minimum size subarray with condition
```

---

## Most Important Condition

Variable Sliding Window works best when the array has:

```txt
positive numbers
non-negative numbers
```

Why?

Because when we move `right`, the sum usually increases.

When we move `left`, the sum usually decreases.

This makes the window predictable.

Important:

```txt
If array has negative numbers, normal sliding window may not work.
```

For negative numbers, many subarray sum problems need:

```txt
Prefix Sum
Prefix Sum + HashMap
```

Those patterns will come later.

---

## Main Variables

| Variable | Meaning |
|---|---|
| `left` | start of current window |
| `right` | end of current window |
| `windowSum` | sum of current window |
| `maxLength` | best maximum length found |
| `minLength` | best minimum length found |

Initial values:

```java
int left = 0;
int windowSum = 0;
```

---

## Core Idea

```txt
right expands the window
left shrinks the window
```

Basic structure:

```java
for (int right = 0; right < nums.length; right++) {
    windowSum += nums[right];

    while (condition is invalid) {
        windowSum -= nums[left];
        left++;
    }

    update answer
}
```

---

## Example Problem: Longest Subarray With Sum <= Target

Problem:

```txt
Find the length of the longest subarray whose sum is less than or equal to target.
```

Input:

```txt
nums = [2, 1, 5, 1, 3, 2]
target = 7
```

Output:

```txt
3
```

Because:

```txt
[1, 5, 1] has sum 7
```

and length:

```txt
3
```

---

## Logic

```txt
Add nums[right] to windowSum
If windowSum becomes greater than target, shrink from left
When windowSum <= target, update maxLength
```

---

## Complete Java Code

```java
class Solution {
    public int longestSubarraySumAtMostK(int[] nums, int target) {
        int left = 0;
        int windowSum = 0;
        int maxLength = 0;

        for (int right = 0; right < nums.length; right++) {
            windowSum += nums[right];

            while (windowSum > target) {
                windowSum -= nums[left];
                left++;
            }

            int length = right - left + 1;

            if (length > maxLength) {
                maxLength = length;
            }
        }

        return maxLength;
    }
}
```

---

## Line-by-Line Explanation

```java
int left = 0;
```

`left` marks the start of the current window.

---

```java
int windowSum = 0;
```

Stores the sum of current window.

---

```java
int maxLength = 0;
```

Stores the longest valid window length found so far.

---

```java
for (int right = 0; right < nums.length; right++)
```

`right` expands the window one element at a time.

---

```java
windowSum += nums[right];
```

Add current element to the window.

---

```java
while (windowSum > target)
```

If the window becomes invalid, shrink it.

---

```java
windowSum -= nums[left];
left++;
```

Remove the leftmost element and move `left` forward.

---

```java
int length = right - left + 1;
```

Calculate current window size.

---

```java
maxLength = Math.max(maxLength, length);
```

Update answer if current valid window is longer.

---

## Why `right - left + 1`?

If:

```txt
left = 1
right = 3
```

Window is:

```txt
indexes 1, 2, 3
```

Length:

```txt
3
```

Formula:

```txt
right - left + 1
3 - 1 + 1 = 3
```

---

## Dry Run

```txt
nums = [2, 1, 5, 1, 3, 2]
target = 7
```

| right | nums[right] | windowSum after add | Invalid? | Action | Window | maxLength |
|---:|---:|---:|---|---|---|---:|
| 0 | 2 | 2 | No | update | [2] | 1 |
| 1 | 1 | 3 | No | update | [2, 1] | 2 |
| 2 | 5 | 8 | Yes | remove 2 | [1, 5] | 2 |
| 3 | 1 | 7 | No | update | [1, 5, 1] | 3 |
| 4 | 3 | 10 | Yes | remove 1, remove 5 | [1, 3] | 3 |
| 5 | 2 | 6 | No | update | [1, 3, 2] | 3 |

Answer:

```txt
3
```

---

## Example 2: Minimum Size Subarray Sum

Problem:

```txt
Find the minimum length subarray whose sum is greater than or equal to target.
```

Input:

```txt
target = 7
nums = [2, 3, 1, 2, 4, 3]
```

Output:

```txt
2
```

Because:

```txt
[4, 3] has sum 7
```

Length:

```txt
2
```

Code:

```java
public int minSubArrayLen(int target, int[] nums) {
    int left = 0;
    int windowSum = 0;
    int minLength = Integer.MAX_VALUE;

    for (int right = 0; right < nums.length; right++) {
        windowSum += nums[right];

        while (windowSum >= target) {
            int length = right - left + 1;

            if (length < minLength) {
                minLength = length;
            }

            windowSum -= nums[left];
            left++;
        }
    }

    if (minLength == Integer.MAX_VALUE) {
        return 0;
    }

    return minLength;
}
```

Important:

```txt
For minimum length, update answer before shrinking.
```

Because the current window is valid.

---

## Example 3: Longest Subarray With At Most K Zeroes

Problem:

```txt
Find longest subarray containing at most k zeroes.
```

Input:

```txt
nums = [1, 1, 0, 0, 1, 1, 1, 0]
k = 1
```

Output:

```txt
4
```

One valid longest window:

```txt
[0, 1, 1, 1]
```

Code:

```java
public int longestOnes(int[] nums, int k) {
    int left = 0;
    int zeroCount = 0;
    int maxLength = 0;

    for (int right = 0; right < nums.length; right++) {
        if (nums[right] == 0) {
            zeroCount++;
        }

        while (zeroCount > k) {
            if (nums[left] == 0) {
                zeroCount--;
            }

            left++;
        }

        int length = right - left + 1;

        if (length > maxLength) {
            maxLength = length;
        }
    }

    return maxLength;
}
```

Here the condition is:

```txt
zeroCount <= k
```

If zeroes become more than `k`, shrink the window.

---

## Example 4: Count Subarrays With Product Less Than K

Problem:

```txt
Count subarrays whose product is less than k.
```

Input:

```txt
nums = [10, 5, 2, 6]
k = 100
```

Output:

```txt
8
```

Valid subarrays:

```txt
[10]
[5]
[2]
[6]
[10, 5]
[5, 2]
[2, 6]
[5, 2, 6]
```

Code:

```java
public int numSubarrayProductLessThanK(int[] nums, int k) {
    if (k <= 1) {
        return 0;
    }

    int left = 0;
    long product = 1;
    int count = 0;

    for (int right = 0; right < nums.length; right++) {
        product *= nums[right];

        while (product >= k) {
            product /= nums[left];
            left++;
        }

        count += right - left + 1;
    }

    return count;
}
```

Why add:

```java
right - left + 1
```

Because every subarray ending at `right` and starting from `left` to `right` is valid.

---

## Variable Window Types

| Problem Type | Window Condition | Answer Update |
|---|---|---|
| Longest valid subarray | Shrink when invalid | update max length |
| Minimum valid subarray | Shrink while valid | update min length before shrinking |
| Count valid subarrays | Shrink when invalid | add `right - left + 1` |
| At most k zeroes | shrink when zeroes > k | update max length |

---

## Time and Space Complexity

For normal variable sliding window:

| Complexity | Value |
|---|---:|
| Time Complexity | O(n) |
| Space Complexity | O(1) |

Why time is O(n)?

```txt
right moves from left to right once
left also moves from left to right once
```

Even though there is a `while` loop inside, every element is added and removed at most once.

So total time is:

```txt
O(n)
```

---

## Common Mistakes

### 1. Using Variable Window for Negative Numbers Without Thinking

If array has negative numbers, window sum may increase or decrease unpredictably.

Example:

```txt
[5, -10, 6]
```

Removing or adding elements does not behave simply.

For such problems, think:

```txt
Prefix Sum
HashMap
```

---

### 2. Forgetting to Shrink the Window

Wrong:

```java
windowSum += nums[right];
```

but never reducing from left.

Correct:

```java
while (windowSum > target) {
    windowSum -= nums[left];
    left++;
}
```

---

### 3. Updating Minimum Length at Wrong Time

For minimum size subarray sum, update while the window is valid:

```java
while (windowSum >= target) {
    minLength = Math.min(minLength, right - left + 1);
    windowSum -= nums[left];
    left++;
}
```

---

### 4. Confusing Fixed and Variable Window

If question says:

```txt
subarray of size k
```

Use:

```txt
Fixed Size Sliding Window
```

If question says:

```txt
longest / smallest subarray with condition
```

Use:

```txt
Variable Size Sliding Window
```

---

### 5. Wrong Length Formula

Correct:

```java
right - left + 1
```

Wrong:

```java
right - left
```

---

## Beginner Checklist

Before applying Variable Size Sliding Window, ask:

```txt
1. Is the problem about a continuous subarray?
2. Is the window size not fixed?
3. Is the question asking longest or smallest?
4. What makes a window valid?
5. What makes a window invalid?
6. When should I expand right?
7. When should I shrink left?
8. Should I update max length or min length?
9. Are array elements positive/non-negative?
10. Will negative numbers break this logic?
```

---

## Pattern Summary

| Point | Meaning |
|---|---|
| Pattern Name | Variable Size Sliding Window |
| Pattern Number | 11 |
| Used For | Longest/smallest/count subarray with condition |
| Main Variables | `left`, `right`, window value |
| Expand | Move `right` |
| Shrink | Move `left` |
| Common Time | O(n) |
| Common Space | O(1) |
| Important Condition | Works best with positive/non-negative values |

---

## Next Pattern

```txt
Pattern 12: Prefix Sum
```
