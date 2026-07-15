# Day 12 Practice: Pattern 10 Fixed Size Sliding Window

Today's goal is to master the **Fixed Size Sliding Window Pattern**.

This pattern is used when the problem asks about continuous subarrays of fixed size `k`.

---

## Practice Method

For every problem, write:

```txt
Given:
Asked:
Is it a subarray?
Is window size fixed?
What is k?
What should each window calculate?
Pattern:
Return:
Time Complexity:
Space Complexity:
```

Example:

```txt
Problem: Maximum sum of subarray of size k

Given: integer array
Asked: maximum sum of any subarray of size k
Is it a subarray? yes
Is window size fixed? yes
What is k? 3
What should each window calculate? sum
Pattern: Fixed Size Sliding Window
Return: maximum sum
Time: O(n)
Space: O(1)
```

---

## Manual Practice Problems

### 1. Maximum Sum of Size K

```txt
Input: nums = [2, 1, 5, 1, 3, 2], k = 3
Output: 9
```

Think:

```txt
Best window is [5, 1, 3].
```

---

### 2. Minimum Sum of Size K

```txt
Input: nums = [3, 2, 1, 5, 4], k = 2
Output: 3
```

Think:

```txt
Minimum sum window is [2, 1].
```

---

### 3. Maximum Average Subarray

```txt
Input: nums = [1, 12, -5, -6, 50, 3], k = 4
Output: 12.75
```

Think:

```txt
Find max sum first.
Then divide by k.
```

---

### 4. Count Windows Greater Than X

```txt
Input: nums = [2, 1, 5, 1, 3, 2], k = 3, x = 6
Output: 3
```

Think:

```txt
Count windows whose sum is greater than 6.
```

---

### 5. Count Windows With Exact Sum X

```txt
Input: nums = [1, 2, 1, 3, 2], k = 2, x = 3
Output: 2
```

Valid windows:

```txt
[1, 2]
[2, 1]
```

---

### 6. Print All Window Sums

```txt
Input: nums = [1, 2, 3, 4], k = 2
Output: 3, 5, 7
```

Windows:

```txt
[1, 2] → 3
[2, 3] → 5
[3, 4] → 7
```

---

### 7. First Negative Number in Every Window

```txt
Input:
nums = [12, -1, -7, 8, -15, 30, 16, 28]
k = 3

Output:
[-1, -1, -7, -15, -15, 0]
```

Think:

```txt
Use queue to store indexes of negative numbers.
```

---

### 8. Max Sum With Negative Numbers

```txt
Input: nums = [-2, -3, -1, -5], k = 2
Output: -4
```

Why?

```txt
[-3, -1] has sum -4
```

Important:

```txt
Initialize maxSum using first window, not 0.
```

---

## Dry Run Practice

Dry run:

```txt
nums = [2, 1, 5, 1, 3, 2]
k = 3
```

Fill this table:

| i | nums[i] | Add | Remove | windowSum | maxSum |
|---:|---:|---:|---:|---:|---:|
| 0 |  |  |  |  |  |
| 1 |  |  |  |  |  |
| 2 |  |  |  |  |  |
| 3 |  |  |  |  |  |
| 4 |  |  |  |  |  |
| 5 |  |  |  |  |  |

---

## Completed Dry Run Answer

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

---

## Common Mistake Practice

### Mistake 1

Find the issue:

```java
for (int i = 0; i <= k; i++) {
    windowSum += nums[i];
}
```

Problem:

```txt
This adds k + 1 elements.
```

Correct:

```java
for (int i = 0; i < k; i++)
```

---

### Mistake 2

Find the issue:

```java
windowSum += nums[i];
```

while sliding, but never removing old value.

Problem:

```txt
Window size keeps increasing.
```

Correct:

```java
windowSum = windowSum - nums[i - k] + nums[i];
```

---

### Mistake 3

Find the issue:

```java
return maxSum / k;
```

for average.

Problem:

```txt
Integer division may remove decimal value.
```

Correct:

```java
return (double) maxSum / k;
```

---

### Mistake 4

Find the issue:

```java
int maxSum = 0;
```

for arrays that may contain all negative numbers.

Problem:

```txt
0 may not be a valid window sum.
```

Better:

```txt
Initialize maxSum with the first window sum.
```

---

### Mistake 5

Find the issue:

```txt
Question asks for longest subarray.
```

Mistake:

```txt
Using fixed size sliding window.
```

Correct:

```txt
Longest/smallest subarray usually needs variable size sliding window.
```

---

## LeetCode Practice

| No. | Problem | Concept |
|---:|---|---|
| 643 | Maximum Average Subarray I | Fixed window sum |
| 1343 | Number of Sub-arrays of Size K and Average Greater than or Equal to Threshold | Fixed window count |
| 1456 | Maximum Number of Vowels in a Substring of Given Length | Fixed window count |
| 1052 | Grumpy Bookstore Owner | Fixed window gain |
| 2379 | Minimum Recolors to Get K Consecutive Black Blocks | Fixed window minimum |
| 2090 | K Radius Subarray Averages | Fixed window / prefix idea |
| 1423 | Maximum Points You Can Obtain from Cards | Fixed window reverse thinking |

---

## Answer Key

| Problem | Pattern | Time | Space |
|---:|---|---:|---:|
| 1 | Fixed Sliding Window | O(n) | O(1) |
| 2 | Fixed Sliding Window | O(n) | O(1) |
| 3 | Fixed Sliding Window | O(n) | O(1) |
| 4 | Fixed Sliding Window | O(n) | O(1) |
| 5 | Fixed Sliding Window | O(n) | O(1) |
| 6 | Fixed Sliding Window | O(n) | O(1) |
| 7 | Fixed Sliding Window + Queue | O(n) | O(k) |
| 8 | Fixed Sliding Window | O(n) | O(1) |

---

## Before Moving to Pattern 11

You should be able to:

| Skill | Status |
|---|---|
| Explain fixed size sliding window | ✅ |
| Identify subarray of size `k` problems | ✅ |
| Calculate first window | ✅ |
| Slide by removing outgoing and adding incoming | ✅ |
| Find max sum of size `k` | ✅ |
| Find min sum of size `k` | ✅ |
| Calculate maximum average | ✅ |
| Count valid windows | ✅ |
| Handle negative numbers correctly | ✅ |
| Explain O(n) time | ✅ |
| Know difference between fixed and variable window | ✅ |

---

## Next Topic

```txt
Pattern 11: Variable Size Sliding Window
```
