# Pattern 10: Fixed Size Sliding Window

Fixed Size Sliding Window is an array pattern used when we need to process every continuous subarray of a fixed length `k`.

It helps us avoid recalculating the same work again and again.

---

## What Is a Window?

A window means a continuous part of an array.

Example:

```txt
nums = [2, 1, 5, 1, 3, 2]
k = 3
```

All windows of size `3` are:

```txt
[2, 1, 5]
[1, 5, 1]
[5, 1, 3]
[1, 3, 2]
```

Each window has exactly `3` elements.

That is why this is called:

```txt
Fixed Size Sliding Window
```

---

## What Does Sliding Mean?

Sliding means moving the window one step forward.

From:

```txt
[2, 1, 5]
```

Move one step:

```txt
[1, 5, 1]
```

Then:

```txt
[5, 1, 3]
```

Then:

```txt
[1, 3, 2]
```

The window size remains fixed.

Only the position changes.

---

## Simple Meaning

```txt
Take first k elements
Calculate result for this window
Move window forward
Remove left element
Add new right element
Update answer
```

---

## Why Sliding Window Is Needed?

Brute force calculates every window from scratch.

For every window of size `k`, it loops over `k` elements again.

That can take:

```txt
O(n × k)
```

Sliding Window avoids repeated calculation.

It keeps the current window result and updates it in O(1).

So total time becomes:

```txt
O(n)
```

---

## Pattern Signal

Think of Fixed Size Sliding Window when the question says:

```txt
subarray of size k
window of size k
maximum sum of k elements
minimum sum of k elements
average of subarray of size k
consecutive k elements
fixed length subarray
```

Most common signal:

```txt
Subarray of size k
```

---

## Important Word: Subarray

A subarray is a continuous part of an array.

Example:

```txt
nums = [1, 2, 3, 4]
```

Valid subarrays:

```txt
[1, 2]
[2, 3, 4]
[1, 2, 3]
```

Invalid subarray:

```txt
[1, 3]
```

Because `1` and `3` are not continuous.

Sliding Window is mostly used for continuous subarrays.

---

## Fixed Size vs Variable Size Sliding Window

| Type | Window Size | Example |
|---|---|---|
| Fixed Size | Size is given as `k` | Maximum sum of subarray of size `k` |
| Variable Size | Size changes based on condition | Longest subarray with sum at most `k` |

Today we focus only on:

```txt
Fixed Size Sliding Window
```

Variable size sliding window will come next.

---

## Core Idea

For every new window:

```txt
newWindowSum = oldWindowSum - elementGoingOut + elementComingIn
```

Example:

```txt
nums = [2, 1, 5, 1, 3, 2]
k = 3
```

First window:

```txt
[2, 1, 5] → sum = 8
```

Next window:

```txt
[1, 5, 1]
```

Instead of calculating:

```txt
1 + 5 + 1
```

We do:

```txt
old sum - outgoing + incoming
8 - 2 + 1 = 7
```

---

## Main Variables

| Variable | Meaning |
|---|---|
| `k` | fixed window size |
| `windowSum` | sum of current window |
| `maxSum` | best answer so far |
| `i` | loop index |
| `nums[i - k]` | element going out of window |

---

## Basic Fixed Sliding Window Logic

```txt
1. Add current element to window
2. If window size becomes greater than k, remove left element
3. If window size is exactly k, update answer
```

---

## Complete Java Code: Maximum Sum of Subarray of Size K

Problem:

```txt
Find maximum sum of any subarray of size k.
```

Input:

```txt
nums = [2, 1, 5, 1, 3, 2]
k = 3
```

Output:

```txt
9
```

Because:

```txt
[5, 1, 3] has sum 9
```

Code:

```java
class Solution {
    public int maxSumSubarraySizeK(int[] nums, int k) {
        int windowSum = 0;
        int maxSum = Integer.MIN_VALUE;

        for (int i = 0; i < nums.length; i++) {
            windowSum += nums[i];

            if (i >= k) {
                windowSum -= nums[i - k];
            }

            if (i >= k - 1) {
                if (windowSum > maxSum) {
                    maxSum = windowSum;
                }
            }
        }

        return maxSum;
    }
}
```

---

## Line-by-Line Explanation

```java
int windowSum = 0;
```

Stores the sum of the current window.

---

```java
int maxSum = Integer.MIN_VALUE;
```

Stores the maximum window sum found so far.

We use `Integer.MIN_VALUE` because array values can be negative too.

---

```java
for (int i = 0; i < nums.length; i++)
```

Traverse the array from left to right.

---

```java
windowSum += nums[i];
```

Add current element to the window.

---

```java
if (i >= k)
```

When index becomes at least `k`, window size becomes greater than `k`.

So we remove the element that is going out.

---

```java
windowSum -= nums[i - k];
```

Removes the leftmost old element from the window.

---

```java
if (i >= k - 1)
```

This means the first complete window of size `k` is ready.

Example:

```txt
k = 3
first complete window ends at index 2
```

So condition:

```txt
i >= 2
```

which is:

```txt
i >= k - 1
```

---

```java
maxSum = Math.max(maxSum, windowSum);
```

Updates the best answer.

---

## Dry Run: Maximum Sum of Size K

```txt
nums = [2, 1, 5, 1, 3, 2]
k = 3
```

| i | nums[i] | Add | Remove | windowSum | maxSum |
|---:|---:|---:|---:|---:|---:|
| 0 | 2 | +2 | - | 2 | - |
| 1 | 1 | +1 | - | 3 | - |
| 2 | 5 | +5 | - | 8 | 8 |
| 3 | 1 | +1 | -2 | 7 | 8 |
| 4 | 3 | +3 | -1 | 9 | 9 |
| 5 | 2 | +2 | -5 | 6 | 9 |

Answer:

```txt
9
```

Best window:

```txt
[5, 1, 3]
```

---

## Alternative Beginner-Friendly Code

Some beginners understand this version more easily.

Step 1: Calculate first window.

Step 2: Slide the window.

```java
public int maxSumSubarraySizeK(int[] nums, int k) {
    int windowSum = 0;

    for (int i = 0; i < k; i++) {
        windowSum += nums[i];
    }

    int maxSum = windowSum;

    for (int i = k; i < nums.length; i++) {
        windowSum = windowSum - nums[i - k] + nums[i];

        if (windowSum > maxSum) {
            maxSum = windowSum;
        }
    }

    return maxSum;
}
```

Both approaches are correct.

The second one is easier for beginners.

---

## Example 1: Minimum Sum of Subarray of Size K

Problem:

```txt
Find minimum sum of any subarray of size k.
```

Input:

```txt
nums = [3, 2, 1, 5, 4]
k = 2
```

Windows:

```txt
[3, 2] → 5
[2, 1] → 3
[1, 5] → 6
[5, 4] → 9
```

Output:

```txt
3
```

Code:

```java
public int minSumSubarraySizeK(int[] nums, int k) {
    int windowSum = 0;

    for (int i = 0; i < k; i++) {
        windowSum += nums[i];
    }

    int minSum = windowSum;

    for (int i = k; i < nums.length; i++) {
        windowSum = windowSum - nums[i - k] + nums[i];

        if (windowSum < minSum) {
            minSum = windowSum;
        }
    }

    return minSum;
}
```

---

## Example 2: Maximum Average Subarray

Problem:

```txt
Find maximum average of any subarray of size k.
```

Input:

```txt
nums = [1, 12, -5, -6, 50, 3]
k = 4
```

Output:

```txt
12.75
```

Idea:

```txt
Maximum average = maximum sum / k
```

Code:

```java
public double findMaxAverage(int[] nums, int k) {
    int windowSum = 0;

    for (int i = 0; i < k; i++) {
        windowSum += nums[i];
    }

    int maxSum = windowSum;

    for (int i = k; i < nums.length; i++) {
        windowSum = windowSum - nums[i - k] + nums[i];

        if (windowSum > maxSum) {
            maxSum = windowSum;
        }
    }

    return (double) maxSum / k;
}
```

---

## Example 3: Count Windows With Sum Greater Than X

Problem:

```txt
Count subarrays of size k whose sum is greater than x.
```

Input:

```txt
nums = [2, 1, 5, 1, 3, 2]
k = 3
x = 6
```

Window sums:

```txt
[2, 1, 5] → 8
[1, 5, 1] → 7
[5, 1, 3] → 9
[1, 3, 2] → 6
```

Sums greater than `6`:

```txt
8, 7, 9
```

Output:

```txt
3
```

Code:

```java
public int countWindowsGreaterThanX(int[] nums, int k, int x) {
    int windowSum = 0;

    for (int i = 0; i < k; i++) {
        windowSum += nums[i];
    }

    int count = 0;

    if (windowSum > x) {
        count++;
    }

    for (int i = k; i < nums.length; i++) {
        windowSum = windowSum - nums[i - k] + nums[i];

        if (windowSum > x) {
            count++;
        }
    }

    return count;
}
```

---

## Example 4: First Negative Number in Every Window

Problem:

```txt
Find first negative number in every window of size k.
```

Input:

```txt
nums = [12, -1, -7, 8, -15, 30, 16, 28]
k = 3
```

Output:

```txt
[-1, -1, -7, -15, -15, 0]
```

Here `0` means no negative number in that window.

This problem is a slightly advanced fixed window problem.

It uses a queue to remember negative numbers.

Code:

```java
import java.util.LinkedList;
import java.util.Queue;

public int[] firstNegativeInWindow(int[] nums, int k) {
    Queue<Integer> queue = new LinkedList<>();
    int[] result = new int[nums.length - k + 1];

    int index = 0;

    for (int i = 0; i < nums.length; i++) {
        if (nums[i] < 0) {
            queue.add(i);
        }

        if (!queue.isEmpty() && queue.peek() <= i - k) {
            queue.remove();
        }

        if (i >= k - 1) {
            if (!queue.isEmpty()) {
                result[index] = nums[queue.peek()];
            }
            else {
                result[index] = 0;
            }

            index++;
        }
    }

    return result;
}
```

Why store indexes?

```txt
Because we need to know when a negative number goes out of the window.
```

---

## Time and Space Complexity

For normal fixed-size sum window:

| Complexity | Value |
|---|---:|
| Time Complexity | O(n) |
| Space Complexity | O(1) |

For first negative in every window:

| Complexity | Value |
|---|---:|
| Time Complexity | O(n) |
| Space Complexity | O(k) |

Because the queue may store indexes of elements inside the window.

---

## Brute Force vs Sliding Window

| Point | Brute Force | Sliding Window |
|---|---|---|
| Work | Recalculates every window | Reuses previous window result |
| Time | O(n × k) | O(n) |
| Space | O(1) | O(1) usually |
| Best for | Very small input | Fixed window problems |

---

## Common Mistakes

### 1. Confusing Subarray and Subsequence

Sliding Window works on continuous elements.

Valid:

```txt
[1, 2, 3]
```

Invalid if skipping elements:

```txt
[1, 3, 5]
```

---

### 2. Forgetting to Remove Outgoing Element

Wrong:

```java
windowSum += nums[i];
```

without removing old element.

Correct:

```java
windowSum = windowSum - nums[i - k] + nums[i];
```

---

### 3. Wrong First Window Size

For first window, loop should run:

```java
i < k
```

not:

```java
i <= k
```

---

### 4. Wrong Average Calculation

Wrong:

```java
return maxSum / k;
```

This may do integer division.

Correct:

```java
return (double) maxSum / k;
```

---

### 5. Using Sliding Window When Size Is Not Fixed

If the question says:

```txt
longest subarray
smallest subarray
sum at most k
sum greater than equal to k
```

The window size may be variable.

That is the next pattern.

---

## Beginner Checklist

Before applying Fixed Size Sliding Window, ask:

```txt
1. Is the problem about subarray?
2. Is the subarray size fixed?
3. Is k given?
4. What should I calculate for each window?
5. Can I update answer by removing one element and adding one element?
6. Do I need maximum, minimum, average, or count?
7. Is the window continuous?
8. What happens when k is greater than array length?
9. What is the time complexity?
```

---

## Pattern Summary

| Point | Meaning |
|---|---|
| Pattern Name | Fixed Size Sliding Window |
| Pattern Number | 10 |
| Used For | Fixed length subarray problems |
| Main Signal | Subarray/window of size `k` |
| Main Logic | Add new element, remove old element |
| Common Variables | `k`, `windowSum`, `maxSum` |
| Time | O(n) |
| Space | O(1) usually |
| Next Pattern | Variable Size Sliding Window |

---

## Next Pattern

```txt
Pattern 11: Variable Size Sliding Window
```
