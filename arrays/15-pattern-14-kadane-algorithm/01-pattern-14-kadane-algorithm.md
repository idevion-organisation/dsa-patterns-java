# Pattern 14: Kadane's Algorithm

Kadane's Algorithm is an array pattern used to find the maximum sum of a continuous subarray.

It is one of the most important patterns for subarray problems.

---

## What Problem Does Kadane's Algorithm Solve?

Suppose we have:

```txt
nums = [-2, 1, -3, 4, -1, 2, 1, -5, 4]
```

We need to find the maximum sum of any continuous subarray.

The best subarray is:

```txt
[4, -1, 2, 1]
```

Sum:

```txt
4 + (-1) + 2 + 1 = 6
```

Answer:

```txt
6
```

---

## Important Word: Subarray

A subarray means a continuous part of an array.

Example:

```txt
nums = [1, 2, 3, 4]
```

Valid subarrays:

```txt
[1]
[1, 2]
[2, 3]
[2, 3, 4]
```

Invalid:

```txt
[1, 3]
```

Because `1` and `3` are not continuous.

Kadane's Algorithm works on continuous subarrays.

---

## Simple Meaning

Kadane's Algorithm means:

```txt
At every index, decide:

Should I continue the previous subarray?
or
Should I start a new subarray from current element?
```

This is the whole idea.

---

## Pattern Signal

Think of Kadane's Algorithm when the question says:

```txt
maximum subarray sum
largest subarray sum
continuous subarray
maximum sum of contiguous elements
best possible subarray sum
subarray with highest sum
```

Most common signal:

```txt
Maximum sum subarray
```

---

## Why Not Brute Force?

Brute force checks all possible subarrays.

Example:

```txt
nums = [1, 2, 3]
```

All subarrays:

```txt
[1]
[1, 2]
[1, 2, 3]
[2]
[2, 3]
[3]
```

For every subarray, we calculate sum.

That can take:

```txt
O(n²)
```

or even:

```txt
O(n³)
```

if sum is calculated again and again.

Kadane's Algorithm solves it in:

```txt
O(n)
```

---

## Core Idea

At each index:

```txt
currentSum = best subarray sum ending at current index
maxSum = best subarray sum found so far
```

For every element, we decide:

```txt
Continue previous subarray:
currentSum + nums[i]

Start new subarray:
nums[i]
```

So:

```txt
currentSum = max(nums[i], currentSum + nums[i])
maxSum = max(maxSum, currentSum)
```

---

## Main Variables

| Variable | Meaning |
|---|---|
| `currentSum` | best sum of subarray ending at current index |
| `maxSum` | best answer found so far |
| `nums[i]` | current element |

---

## Kadane's Algorithm Formula

```java
currentSum = Math.max(nums[i], currentSum + nums[i]);
maxSum = Math.max(maxSum, currentSum);
```

Meaning:

```txt
Either start new from nums[i]
or continue previous subarray
```

---

## Complete Java Code

Problem:

```txt
Find maximum subarray sum.
```

Code:

```java
class Solution {
    public int maxSubArray(int[] nums) {
        int currentSum = nums[0];
        int maxSum = nums[0];

        for (int i = 1; i < nums.length; i++) {
            currentSum = Math.max(nums[i], currentSum + nums[i]);
            maxSum = Math.max(maxSum, currentSum);
        }

        return maxSum;
    }
}
```

---

## Why Start From `nums[0]`?

We use:

```java
int currentSum = nums[0];
int maxSum = nums[0];
```

instead of:

```java
int currentSum = 0;
int maxSum = 0;
```

Because the array may contain all negative numbers.

Example:

```txt
nums = [-5, -2, -8]
```

Correct answer:

```txt
-2
```

If we initialize with `0`, answer may incorrectly become `0`.

So beginner-safe rule:

```txt
Initialize currentSum and maxSum with nums[0].
```

---

## Line-by-Line Explanation

```java
int currentSum = nums[0];
```

The best subarray ending at the first index is the first element itself.

---

```java
int maxSum = nums[0];
```

The best answer so far is also the first element.

---

```java
for (int i = 1; i < nums.length; i++)
```

Start from index `1` because index `0` is already used.

---

```java
currentSum = Math.max(nums[i], currentSum + nums[i]);
```

Decide whether to start new subarray or continue old subarray.

---

```java
maxSum = Math.max(maxSum, currentSum);
```

Update the best answer.

---

```java
return maxSum;
```

Return maximum subarray sum.

---

## Dry Run

```txt
nums = [-2, 1, -3, 4, -1, 2, 1, -5, 4]
```

Initial:

```txt
currentSum = -2
maxSum = -2
```

| i | nums[i] | currentSum + nums[i] | Start New? | currentSum | maxSum |
|---:|---:|---:|---|---:|---:|
| 1 | 1 | -1 | Yes, start from 1 | 1 | 1 |
| 2 | -3 | -2 | No, continue | -2 | 1 |
| 3 | 4 | 2 | Yes, start from 4 | 4 | 4 |
| 4 | -1 | 3 | No, continue | 3 | 4 |
| 5 | 2 | 5 | No, continue | 5 | 5 |
| 6 | 1 | 6 | No, continue | 6 | 6 |
| 7 | -5 | 1 | No, continue | 1 | 6 |
| 8 | 4 | 5 | No, continue | 5 | 6 |

Answer:

```txt
6
```

Best subarray:

```txt
[4, -1, 2, 1]
```

---

## Another Beginner-Friendly Version

Some beginners understand this version better.

Idea:

```txt
Keep adding elements.
If currentSum becomes negative, reset it.
```

Code:

```java
public int maxSubArray(int[] nums) {
    int maxSum = nums[0];
    int currentSum = 0;

    for (int i = 0; i < nums.length; i++) {
        currentSum += nums[i];

        if (currentSum > maxSum) {
            maxSum = currentSum;
        }

        if (currentSum < 0) {
            currentSum = 0;
        }
    }

    return maxSum;
}
```

Why reset when `currentSum < 0`?

```txt
A negative sum will reduce the future subarray sum.
So we drop it and start fresh.
```

Important:

```txt
maxSum must still start from nums[0]
```

so all-negative arrays are handled correctly.

---

## Kadane's Algorithm Intuition

If current sum becomes negative:

```txt
currentSum < 0
```

then it is harmful for the next elements.

Example:

```txt
currentSum = -5
next element = 10
```

Continuing gives:

```txt
-5 + 10 = 5
```

Starting fresh gives:

```txt
10
```

So starting fresh is better.

That is why Kadane's Algorithm drops negative running sums.

---

## Example 1: All Positive Numbers

Input:

```txt
nums = [1, 2, 3, 4]
```

Maximum subarray:

```txt
[1, 2, 3, 4]
```

Output:

```txt
10
```

Because all numbers are positive, the best answer is the whole array.

---

## Example 2: All Negative Numbers

Input:

```txt
nums = [-8, -3, -6, -2, -5]
```

Maximum subarray:

```txt
[-2]
```

Output:

```txt
-2
```

Important:

```txt
For all negative numbers, choose the least negative number.
```

That is why initialization matters.

---

## Example 3: Mixed Positive and Negative Numbers

Input:

```txt
nums = [5, -2, 3, -1, 2]
```

Maximum subarray:

```txt
[5, -2, 3, -1, 2]
```

Output:

```txt
7
```

Even though negatives are present, they may still be part of the best subarray if surrounding positives make the total bigger.

---

## Example 4: Return Maximum Sum With Subarray Indexes

Sometimes the question asks:

```txt
Return the start and end index of maximum sum subarray.
```

Code:

```java
public int[] maxSubArrayWithIndexes(int[] nums) {
    int currentSum = nums[0];
    int maxSum = nums[0];

    int start = 0;
    int end = 0;
    int tempStart = 0;

    for (int i = 1; i < nums.length; i++) {
        if (nums[i] > currentSum + nums[i]) {
            currentSum = nums[i];
            tempStart = i;
        }
        else {
            currentSum = currentSum + nums[i];
        }

        if (currentSum > maxSum) {
            maxSum = currentSum;
            start = tempStart;
            end = i;
        }
    }

    return new int[]{maxSum, start, end};
}
```

Return format:

```txt
[maxSum, startIndex, endIndex]
```

Example:

```txt
nums = [-2, 1, -3, 4, -1, 2, 1, -5, 4]
```

Output:

```txt
[6, 3, 6]
```

Because best subarray is:

```txt
index 3 to 6 → [4, -1, 2, 1]
```

---

## Example 5: Minimum Subarray Sum

Kadane's idea can also find minimum subarray sum.

Instead of maximum, we track minimum.

Code:

```java
public int minSubArray(int[] nums) {
    int currentSum = nums[0];
    int minSum = nums[0];

    for (int i = 1; i < nums.length; i++) {
        currentSum = Math.min(nums[i], currentSum + nums[i]);
        minSum = Math.min(minSum, currentSum);
    }

    return minSum;
}
```

Use this when question asks:

```txt
minimum subarray sum
smallest continuous sum
```

---

## Example 6: Maximum Absolute Subarray Sum

Problem:

```txt
Find maximum absolute sum of any subarray.
```

Idea:

```txt
Maximum absolute sum = max(maxSubarraySum, absolute(minSubarraySum))
```

Code:

```java
public int maxAbsoluteSum(int[] nums) {
    int maxCurrent = nums[0];
    int maxSum = nums[0];

    int minCurrent = nums[0];
    int minSum = nums[0];

    for (int i = 1; i < nums.length; i++) {
        maxCurrent = Math.max(nums[i], maxCurrent + nums[i]);
        maxSum = Math.max(maxSum, maxCurrent);

        minCurrent = Math.min(nums[i], minCurrent + nums[i]);
        minSum = Math.min(minSum, minCurrent);
    }

    return Math.max(Math.abs(maxSum), Math.abs(minSum));
}
```

---

## Kadane's Algorithm vs Sliding Window

| Point | Sliding Window | Kadane's Algorithm |
|---|---|---|
| Used for | Window/subarray with condition | Maximum subarray sum |
| Window size | Fixed or variable | Decided automatically |
| Negative numbers | Can be tricky | Handles negatives well |
| Main idea | Expand/shrink window | Continue or restart subarray |
| Common question | Sum of size k | Maximum subarray sum |

---

## Kadane's Algorithm vs Prefix Sum

| Point | Prefix Sum | Kadane's Algorithm |
|---|---|---|
| Used for | Range sums, subarray sum queries | Maximum subarray sum |
| Needs HashMap? | Sometimes | No |
| Handles negatives | Yes | Yes |
| Best for | Exact sum / queries | Best possible sum |
| Time | O(n) | O(n) |

---

## Time and Space Complexity

| Complexity | Value |
|---|---:|
| Time Complexity | O(n) |
| Space Complexity | O(1) |

Why time is O(n)?

```txt
We scan the array once.
```

Why space is O(1)?

```txt
We only use a few variables.
```

---

## Common Mistakes

### 1. Initializing `maxSum` with 0

Wrong:

```java
int maxSum = 0;
```

This fails for all negative arrays.

Correct:

```java
int maxSum = nums[0];
```

---

### 2. Thinking Kadane's Algorithm Gives Subsequence

Kadane works for:

```txt
subarray
```

not:

```txt
subsequence
```

Subarray must be continuous.

---

### 3. Resetting Without Updating Answer

Wrong:

```java
if (currentSum < 0) {
    currentSum = 0;
}

maxSum = Math.max(maxSum, currentSum);
```

Better:

```java
maxSum = Math.max(maxSum, currentSum);

if (currentSum < 0) {
    currentSum = 0;
}
```

Update answer before resetting.

---

### 4. Ignoring All-Negative Case

Example:

```txt
nums = [-3, -1, -2]
```

Answer should be:

```txt
-1
```

not:

```txt
0
```

---

### 5. Confusing Maximum Element With Maximum Subarray

Maximum element is only one value.

Maximum subarray can include many values.

Example:

```txt
nums = [4, -1, 2, 1]
```

Maximum element:

```txt
4
```

Maximum subarray sum:

```txt
6
```

---

## Beginner Checklist

Before applying Kadane's Algorithm, ask:

```txt
1. Is the question asking maximum subarray sum?
2. Is the subarray continuous?
3. Are negative numbers present?
4. Do I need only sum or also indexes?
5. Should I continue previous subarray or start new?
6. Did I initialize with nums[0]?
7. Am I handling all-negative arrays?
8. Is this exact sum problem or maximum sum problem?
9. Should I use Prefix Sum + HashMap instead?
```

---

## Pattern Summary

| Point | Meaning |
|---|---|
| Pattern Name | Kadane's Algorithm |
| Pattern Number | 14 |
| Used For | Maximum subarray sum |
| Main Decision | Continue or start new |
| Main Variables | `currentSum`, `maxSum` |
| Formula | `currentSum = max(nums[i], currentSum + nums[i])` |
| Time | O(n) |
| Space | O(1) |
| Handles Negative Numbers | Yes |
| Common Problem | Maximum Subarray |

---

## Next Pattern

```txt
Pattern 15: Stock Profit Pattern
```
