# Day 13 Practice: Pattern 11 Variable Size Sliding Window

Today's goal is to master the **Variable Size Sliding Window Pattern**.

This pattern is used when the subarray size is not fixed and changes based on a condition.

---

## Practice Method

For every problem, write:

```txt
Given:
Asked:
Is it a subarray?
Is window size fixed or variable?
What makes window valid?
What makes window invalid?
Pattern:
Return:
Time Complexity:
Space Complexity:
```

Example:

```txt
Problem: Longest subarray with sum <= k

Given: non-negative integer array
Asked: longest valid subarray length
Is it a subarray? yes
Is window size fixed or variable? variable
Valid: windowSum <= k
Invalid: windowSum > k
Pattern: Variable Size Sliding Window
Return: max length
Time: O(n)
Space: O(1)
```

---

## Manual Practice Problems

### 1. Longest Subarray Sum At Most K

```txt
Input:
nums = [2, 1, 5, 1, 3, 2]
k = 7

Output:
3
```

Why?

```txt
[1, 5, 1] has sum 7 and length 3.
```

---

### 2. Minimum Size Subarray Sum

```txt
Input:
target = 7
nums = [2, 3, 1, 2, 4, 3]

Output:
2
```

Why?

```txt
[4, 3] has sum 7.
```

---

### 3. No Valid Minimum Subarray

```txt
Input:
target = 20
nums = [1, 2, 3, 4]

Output:
0
```

Think:

```txt
No subarray sum reaches 20.
```

---

### 4. Longest Subarray With At Most K Zeroes

```txt
Input:
nums = [1, 1, 0, 0, 1, 1, 1, 0]
k = 1

Output:
4
```

Think:

```txt
Shrink when zeroCount > k.
```

---

### 5. Count Subarrays With Product Less Than K

```txt
Input:
nums = [10, 5, 2, 6]
k = 100

Output:
8
```

Think:

```txt
Shrink while product >= k.
```

---

### 6. Count Subarrays Sum At Most K

```txt
Input:
nums = [1, 2, 1, 1]
k = 3

Output:
7
```

Valid subarrays:

```txt
[1]
[2]
[1]
[1]
[1, 2]
[2, 1]
[1, 1]
```

---

### 7. Longest Subarray With At Most K Distinct Values

```txt
Input:
nums = [1, 2, 1, 2, 3]
k = 2

Output:
4
```

Why?

```txt
[1, 2, 1, 2] has at most 2 distinct values.
```

---

### 8. Fixed or Variable Identification

Identify the pattern:

```txt
A. Maximum sum of subarray of size 3
B. Longest subarray with sum <= 10
C. Minimum length subarray with sum >= 7
D. Count subarrays of size 4 with average >= 5
```

Answer:

```txt
A → Fixed Size Sliding Window
B → Variable Size Sliding Window
C → Variable Size Sliding Window
D → Fixed Size Sliding Window
```

---

## Dry Run Practice

Dry run this manually:

```txt
nums = [2, 1, 5, 1, 3, 2]
target = 7
```

Fill this table:

| right | nums[right] | windowSum after add | Invalid? | Action | left | maxLength |
|---:|---:|---:|---|---|---:|---:|
| 0 |  |  |  |  |  |  |
| 1 |  |  |  |  |  |  |
| 2 |  |  |  |  |  |  |
| 3 |  |  |  |  |  |  |
| 4 |  |  |  |  |  |  |
| 5 |  |  |  |  |  |  |

---

## Completed Dry Run Answer

```txt
nums = [2, 1, 5, 1, 3, 2]
target = 7
```

| right | nums[right] | windowSum after add | Invalid? | Action | left | maxLength |
|---:|---:|---:|---|---|---:|---:|
| 0 | 2 | 2 | No | update length | 0 | 1 |
| 1 | 1 | 3 | No | update length | 0 | 2 |
| 2 | 5 | 8 | Yes | remove 2 | 1 | 2 |
| 3 | 1 | 7 | No | update length | 1 | 3 |
| 4 | 3 | 10 | Yes | remove 1, remove 5 | 3 | 3 |
| 5 | 2 | 6 | No | update length | 3 | 3 |

Answer:

```txt
3
```

---

## Common Mistake Practice

### Mistake 1

Find the issue:

```java
if (windowSum > k) {
    windowSum -= nums[left];
    left++;
}
```

Problem:

```txt
Sometimes one removal is not enough.
```

Correct:

```java
while (windowSum > k) {
    windowSum -= nums[left];
    left++;
}
```

---

### Mistake 2

Find the issue:

```java
int length = right - left;
```

Problem:

```txt
Length formula is wrong.
```

Correct:

```java
int length = right - left + 1;
```

---

### Mistake 3

Find the issue:

```java
int minLength = 0;
```

for minimum size subarray.

Problem:

```txt
0 will always look like the smallest length.
```

Correct:

```java
int minLength = Integer.MAX_VALUE;
```

---

### Mistake 4

Find the issue:

```txt
Array contains negative numbers, but normal sliding window is used for sum condition.
```

Problem:

```txt
Negative numbers can break predictable shrinking logic.
```

Better:

```txt
Think Prefix Sum or Prefix Sum + HashMap.
```

---

### Mistake 5

Find the issue:

```txt
Question says subarray of size k.
```

Mistake:

```txt
Using variable size sliding window.
```

Correct:

```txt
Use Fixed Size Sliding Window.
```

---

## LeetCode Practice

| No. | Problem | Concept |
|---:|---|---|
| 209 | Minimum Size Subarray Sum | Minimum variable window |
| 1004 | Max Consecutive Ones III | At most k zeroes |
| 713 | Subarray Product Less Than K | Product window |
| 904 | Fruit Into Baskets | At most 2 distinct values |
| 424 | Longest Repeating Character Replacement | Variable window |
| 3 | Longest Substring Without Repeating Characters | Variable window + set/map |
| 1493 | Longest Subarray of 1's After Deleting One Element | At most one zero |
| 2024 | Maximize the Confusion of an Exam | At most k changes |

---

## Answer Key

| Problem | Pattern | Time | Space |
|---:|---|---:|---:|
| 1 | Variable Sliding Window | O(n) | O(1) |
| 2 | Variable Sliding Window | O(n) | O(1) |
| 3 | Variable Sliding Window | O(n) | O(1) |
| 4 | Variable Sliding Window | O(n) | O(1) |
| 5 | Variable Sliding Window | O(n) | O(1) |
| 6 | Variable Sliding Window | O(n) | O(1) |
| 7 | Sliding Window + HashMap | O(n) | O(k) |
| 8 | Pattern Identification | - | - |

---

## Before Moving to Pattern 12

You should be able to:

| Skill | Status |
|---|---|
| Explain variable size sliding window | ✅ |
| Identify longest/smallest subarray problems | ✅ |
| Use `left` and `right` pointers | ✅ |
| Expand window using `right` | ✅ |
| Shrink window using `left` | ✅ |
| Write invalid condition clearly | ✅ |
| Calculate length using `right - left + 1` | ✅ |
| Solve minimum size subarray sum | ✅ |
| Solve at most k zeroes | ✅ |
| Know when negative numbers can break sliding window | ✅ |
| Explain O(n) time | ✅ |

---

## Next Topic

```txt
Pattern 12: Prefix Sum
```
