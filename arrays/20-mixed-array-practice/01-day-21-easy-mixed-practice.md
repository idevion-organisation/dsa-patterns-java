# Day 21: Easy Mixed Array Practice

Day 21 starts the mixed practice phase.

Till Day 20, every topic was learned pattern by pattern.

Now the goal is different:

```txt
Read problem → identify pattern → explain why → solve
```

This is the real DSA skill.

---

## Goal of Day 21

Today you will practice easy array problems from mixed patterns.

You should not solve by memorizing.

You should solve by identifying:

```txt
What is the problem asking?
Which pattern fits?
Why does that pattern fit?
What is the time complexity?
```

---

## Practice Rule

For every problem, write this before coding:

```txt
Given:
Asked:
Important signal:
Pattern:
Why this pattern:
Approach:
Time Complexity:
Space Complexity:
```

Example:

```txt
Problem: Contains Duplicate

Given: integer array
Asked: check if any duplicate exists
Important signal: duplicate / already appeared
Pattern: HashSet
Why this pattern: HashSet can track seen elements
Approach: add elements to set, if already exists return true
Time Complexity: O(n)
Space Complexity: O(n)
```

---

# Easy Mixed Practice Problems

---

## Problem 1: Find Maximum Element

```txt
Input:
nums = [3, 7, 2, 9, 5]

Output:
9
```

Pattern:

```txt
Traversal
```

Why?

```txt
Need to visit every element and track maximum.
```

---

## Problem 2: Find Target in Unsorted Array

```txt
Input:
nums = [4, 8, 2, 9, 1]
target = 9

Output:
3
```

Pattern:

```txt
Linear Search
```

Why?

```txt
Array is unsorted, so check elements one by one.
```

---

## Problem 3: Binary Search

```txt
Input:
nums = [1, 3, 5, 7, 9]
target = 7

Output:
3
```

Pattern:

```txt
Binary Search
```

Why?

```txt
Array is sorted and target needs to be searched.
```

---

## Problem 4: Contains Duplicate

```txt
Input:
nums = [1, 2, 3, 1]

Output:
true
```

Pattern:

```txt
HashSet
```

Why?

```txt
Need to check if a value appeared before.
```

---

## Problem 5: Count Frequency of Target

```txt
Input:
nums = [1, 2, 2, 3, 2, 4]
target = 2

Output:
3
```

Pattern:

```txt
Traversal
```

Why?

```txt
Only one target frequency is needed, so simple count is enough.
```

---

## Problem 6: Frequency of All Elements

```txt
Input:
nums = [1, 2, 2, 3, 1]

Output:
1 -> 2
2 -> 2
3 -> 1
```

Pattern:

```txt
HashMap Frequency
```

Why?

```txt
Need count of every value.
```

---

## Problem 7: Remove Element

```txt
Input:
nums = [3, 2, 2, 3]
val = 3

Output:
new length = 2
modified nums starts with [2, 2]
```

Pattern:

```txt
In-place Overwrite
```

Why?

```txt
Need to modify same array and keep valid elements.
```

---

## Problem 8: Move Zeroes

```txt
Input:
nums = [0, 1, 0, 3, 12]

Output:
[1, 3, 12, 0, 0]
```

Pattern:

```txt
In-place Overwrite
```

Why?

```txt
Keep non-zero values first, then fill remaining positions with zero.
```

---

## Problem 9: Two Sum in Sorted Array

```txt
Input:
nums = [2, 7, 11, 15]
target = 9

Output:
[0, 1]
```

Pattern:

```txt
Two Pointers
```

Why?

```txt
Array is sorted and pair sum is required.
```

---

## Problem 10: Reverse Array

```txt
Input:
nums = [1, 2, 3, 4, 5]

Output:
[5, 4, 3, 2, 1]
```

Pattern:

```txt
Two Pointers
```

Why?

```txt
Swap from both ends using left and right pointers.
```

---

## Problem 11: Maximum Sum of Subarray Size K

```txt
Input:
nums = [2, 1, 5, 1, 3, 2]
k = 3

Output:
9
```

Pattern:

```txt
Fixed Size Sliding Window
```

Why?

```txt
Subarray size is fixed as k.
```

---

## Problem 12: Longest Subarray Sum At Most K

```txt
Input:
nums = [2, 1, 5, 1, 3, 2]
k = 7

Output:
3
```

Pattern:

```txt
Variable Size Sliding Window
```

Why?

```txt
Need longest subarray and size is not fixed.
```

---

## Problem 13: Running Sum

```txt
Input:
nums = [1, 2, 3, 4]

Output:
[1, 3, 6, 10]
```

Pattern:

```txt
Prefix Sum
```

Why?

```txt
Each index stores sum from start to current index.
```

---

## Problem 14: Range Sum Query

```txt
Input:
nums = [2, 4, 1, 5, 3]
left = 1
right = 3

Output:
10
```

Pattern:

```txt
Prefix Sum
```

Why?

```txt
Need sum from left index to right index.
```

---

## Problem 15: Count Subarrays With Sum K

```txt
Input:
nums = [1, 2, 3]
k = 3

Output:
2
```

Pattern:

```txt
Prefix Sum + HashMap
```

Why?

```txt
Need count of subarrays with exact sum k.
```

---

## Problem 16: Maximum Subarray Sum

```txt
Input:
nums = [-2, 1, -3, 4, -1, 2, 1, -5, 4]

Output:
6
```

Pattern:

```txt
Kadane's Algorithm
```

Why?

```txt
Need maximum sum of continuous subarray.
```

---

## Problem 17: Best Time to Buy and Sell Stock

```txt
Input:
prices = [7, 1, 5, 3, 6, 4]

Output:
5
```

Pattern:

```txt
Stock Profit Pattern
```

Why?

```txt
Need maximum profit by buying before selling.
```

---

## Problem 18: Single Number

```txt
Input:
nums = [4, 1, 2, 1, 2]

Output:
4
```

Pattern:

```txt
XOR
```

Why?

```txt
Every number appears twice except one.
```

---

## Problem 19: Missing Number

```txt
Input:
nums = [3, 0, 1]

Output:
2
```

Pattern:

```txt
Math Formula / XOR
```

Why?

```txt
Numbers are from 0 to n and one number is missing.
```

---

## Problem 20: Matrix Sum

```txt
Input:
matrix = [
  [1, 2],
  [3, 4]
]

Output:
10
```

Pattern:

```txt
Matrix Traversal
```

Why?

```txt
Input is 2D array and every cell must be visited.
```

---

# Day 21 Pattern Summary

| Problem Type | Pattern |
|---|---|
| Find max/min/sum/count | Traversal |
| Search unsorted | Linear Search |
| Search sorted | Binary Search |
| Duplicate check | HashSet |
| Frequency count | HashMap |
| Remove/keep elements | In-place Overwrite |
| Pair in sorted array | Two Pointers |
| Fixed subarray size | Fixed Sliding Window |
| Longest/smallest condition subarray | Variable Sliding Window |
| Range sum | Prefix Sum |
| Exact subarray sum count | Prefix Sum + HashMap |
| Maximum subarray sum | Kadane |
| Stock prices | Stock Profit |
| Pair cancellation | XOR |
| Missing number | Math Formula / XOR |
| 2D input | Matrix |

---

# Day 21 Completion Checklist

You are done with Day 21 when you can:

| Skill | Status |
|---|---|
| Identify pattern before coding | ✅ |
| Explain why the pattern fits | ✅ |
| Solve easy mixed array problems | ✅ |
| Avoid using same pattern everywhere | ✅ |
| Compare similar patterns | ✅ |
| Write time and space complexity | ✅ |
| Dry run at least 5 problems manually | ✅ |

---

## Next Topic

```txt
Day 22: Medium Mixed Array Practice
```
