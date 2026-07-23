# Day 22: Medium Mixed Array Practice

Day 22 is focused on **medium-level mixed array problems**.

Till now, you learned every array pattern separately.

Day 21 tested easy mixed pattern identification.

Now Day 22 moves one level higher:

```txt
Read problem → detect signal → choose pattern → handle edge cases → write optimized code
```

---

## Goal of Day 22

Today’s goal is not only solving problems.

The real goal is:

```txt
Identify the correct pattern when problems are mixed.
```

In real interviews or contests, nobody tells you:

```txt
This is sliding window.
This is prefix sum.
This is HashMap.
This is Kadane.
```

You have to identify it yourself.

---

## Practice Rule

For every problem, write this before coding:

```txt
Given:
Asked:
Important signal:
Possible brute force:
Optimized pattern:
Why this pattern:
Edge cases:
Time Complexity:
Space Complexity:
```

Example:

```txt
Problem: Product Except Self

Given: integer array
Asked: product of all elements except current index
Important signal: without division, product except self
Possible brute force: for every index, multiply all other elements
Optimized pattern: Prefix product + suffix product
Why this pattern: answer[i] depends on left product and right product
Edge cases: zero values
Time Complexity: O(n)
Space Complexity: O(1) extra excluding output
```

---

# Medium Mixed Practice Problems

---

## Problem 1: Search Insert Position

```txt
Input:
nums = [1, 3, 5, 6]
target = 5

Output:
2
```

Pattern:

```txt
Binary Search
```

Why?

```txt
Array is sorted and we need correct index position.
```

Important idea:

```txt
If target is not found, left pointer becomes the insert position.
```

---

## Problem 2: First and Last Position of Element

```txt
Input:
nums = [5, 7, 7, 8, 8, 10]
target = 8

Output:
[3, 4]
```

Pattern:

```txt
Binary Search Variation
```

Why?

```txt
Array is sorted and target may appear multiple times.
Need first and last occurrence.
```

---

## Problem 3: Merge Sorted Array

```txt
Input:
nums1 = [1, 2, 3, 0, 0, 0], m = 3
nums2 = [2, 5, 6], n = 3

Output:
[1, 2, 2, 3, 5, 6]
```

Pattern:

```txt
Merge Sorted Arrays
```

Why?

```txt
Both arrays are sorted.
Need merge in-place from the end.
```

---

## Problem 4: 3Sum

```txt
Input:
nums = [-1, 0, 1, 2, -1, -4]

Output:
[[-1, -1, 2], [-1, 0, 1]]
```

Pattern:

```txt
Sorting + Two Pointers
```

Why?

```txt
Need triplets with sum 0.
After sorting, fix one element and use two pointers for remaining pair.
```

---

## Problem 5: Maximum Product of Two Elements

```txt
Input:
nums = [3, 4, 5, 2]

Output:
12
```

Explanation:

```txt
(5 - 1) * (4 - 1) = 12
```

Pattern:

```txt
Traversal
```

Why?

```txt
Need largest and second largest values.
```

---

## Problem 6: Longest Consecutive Sequence

```txt
Input:
nums = [100, 4, 200, 1, 3, 2]

Output:
4
```

Explanation:

```txt
Longest sequence is [1, 2, 3, 4].
```

Pattern:

```txt
HashSet
```

Why?

```txt
Need quick existence check.
Start only when num - 1 does not exist.
```

---

## Problem 7: Subarray Product Less Than K

```txt
Input:
nums = [10, 5, 2, 6]
k = 100

Output:
8
```

Pattern:

```txt
Variable Size Sliding Window
```

Why?

```txt
Need count of subarrays where product condition is maintained.
Array contains positive numbers.
```

---

## Problem 8: Minimum Size Subarray Sum

```txt
Input:
target = 7
nums = [2, 3, 1, 2, 4, 3]

Output:
2
```

Pattern:

```txt
Variable Size Sliding Window
```

Why?

```txt
Need minimum length subarray whose sum is at least target.
Values are positive.
```

---

## Problem 9: Max Consecutive Ones III

```txt
Input:
nums = [1, 1, 0, 0, 1, 1, 1, 0]
k = 1

Output:
4
```

Pattern:

```txt
Variable Size Sliding Window
```

Why?

```txt
Need longest window with at most k zeroes.
```

---

## Problem 10: Product of Array Except Self

```txt
Input:
nums = [1, 2, 3, 4]

Output:
[24, 12, 8, 6]
```

Pattern:

```txt
Prefix Product + Suffix Product
```

Why?

```txt
Need product except current index without division.
```

---

## Problem 11: Sort Colors

```txt
Input:
nums = [2, 0, 2, 1, 1, 0]

Output:
[0, 0, 1, 1, 2, 2]
```

Pattern:

```txt
Dutch National Flag
```

Why?

```txt
Array contains only 0, 1, and 2.
Need in-place sorting in linear time.
```

---

## Problem 12: Rotate Array

```txt
Input:
nums = [1, 2, 3, 4, 5, 6, 7]
k = 3

Output:
[5, 6, 7, 1, 2, 3, 4]
```

Pattern:

```txt
Rotate Array using Reverse
```

Why?

```txt
Need circular shifting in-place.
```

---

## Problem 13: Subarray Sum Equals K

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
Need count of continuous subarrays with exact sum k.
```

---

## Problem 14: Maximum Subarray Sum

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

## Problem 15: Corporate Flight Bookings

```txt
Input:
bookings = [
  [1, 2, 10],
  [2, 3, 20],
  [2, 5, 25]
]
n = 5

Output:
[10, 55, 45, 25, 25]
```

Pattern:

```txt
Difference Array
```

Why?

```txt
Many range updates need to be applied efficiently.
```

---

## Problem 16: Spiral Matrix

```txt
Input:
matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
]

Output:
[1, 2, 3, 6, 9, 8, 7, 4, 5]
```

Pattern:

```txt
Matrix Boundary Traversal
```

Why?

```txt
Need to traverse matrix layer by layer.
```

---

## Problem 17: Set Matrix Zeroes

```txt
Input:
matrix = [
  [1, 1, 1],
  [1, 0, 1],
  [1, 1, 1]
]

Output:
[
  [1, 0, 1],
  [0, 0, 0],
  [1, 0, 1]
]
```

Pattern:

```txt
Matrix Marking
```

Why?

```txt
If a cell is zero, its entire row and column must become zero.
```

Beginner version uses extra row and column arrays.

---

## Problem 18: Find Pivot Index

```txt
Input:
nums = [1, 7, 3, 6, 5, 6]

Output:
3
```

Pattern:

```txt
Prefix / Total Sum
```

Why?

```txt
Need index where left sum equals right sum.
```

---

## Problem 19: Set Mismatch

```txt
Input:
nums = [1, 2, 2, 4]

Output:
[2, 3]
```

Pattern:

```txt
Frequency Array
```

Why?

```txt
Numbers are from 1 to n.
One number is duplicated and one is missing.
```

---

## Problem 20: Best Time to Buy and Sell Stock II

```txt
Input:
prices = [7, 1, 5, 3, 6, 4]

Output:
7
```

Pattern:

```txt
Stock Profit Multiple Transactions
```

Why?

```txt
Multiple transactions are allowed.
Add every positive difference.
```

---

# Day 22 Medium Pattern Summary

| Problem | Pattern |
|---|---|
| Search Insert Position | Binary Search |
| First and Last Position | Binary Search Variation |
| Merge Sorted Array | Merge Sorted Arrays |
| 3Sum | Sorting + Two Pointers |
| Maximum Product of Two Elements | Traversal |
| Longest Consecutive Sequence | HashSet |
| Subarray Product Less Than K | Variable Sliding Window |
| Minimum Size Subarray Sum | Variable Sliding Window |
| Max Consecutive Ones III | Variable Sliding Window |
| Product Except Self | Prefix + Suffix Product |
| Sort Colors | Dutch National Flag |
| Rotate Array | Reverse Method |
| Subarray Sum Equals K | Prefix Sum + HashMap |
| Maximum Subarray | Kadane |
| Corporate Flight Bookings | Difference Array |
| Spiral Matrix | Matrix Boundary |
| Set Matrix Zeroes | Matrix Marking |
| Pivot Index | Prefix / Total Sum |
| Set Mismatch | Frequency Array |
| Stock II | Stock Profit Multiple Transactions |

---

# Confusion Handling

## Binary Search vs Linear Search

Use Binary Search when:

```txt
Array is sorted
Search space can be divided
```

Use Linear Search when:

```txt
Array is unsorted
No special property exists
```

---

## Sliding Window vs Prefix Sum + HashMap

Use Sliding Window when:

```txt
Window condition can be adjusted by moving left/right
Usually positive or non-negative values
```

Use Prefix Sum + HashMap when:

```txt
Need exact sum k
Negative values may exist
Need count of subarrays
```

---

## Sorting + Two Pointers vs HashMap

Use Sorting + Two Pointers when:

```txt
Pair/triplet sum is needed
Duplicates need to be skipped
Order does not matter
```

Use HashMap when:

```txt
Need quick lookup
Original index may matter
Frequency matters
```

---

## Difference Array vs Prefix Sum

Use Prefix Sum for:

```txt
Range sum queries
```

Use Difference Array for:

```txt
Range update queries
```

---

# Day 22 Completion Checklist

You are done with Day 22 when you can:

| Skill | Status |
|---|---|
| Identify medium array patterns | ✅ |
| Explain why each pattern fits | ✅ |
| Solve Binary Search variations | ✅ |
| Solve Two Pointer after sorting problems | ✅ |
| Use Sliding Window for variable conditions | ✅ |
| Use Prefix Sum + HashMap for exact sum | ✅ |
| Use Difference Array for range updates | ✅ |
| Handle matrix boundary problems | ✅ |
| Write optimized Java code | ✅ |
| Explain time and space complexity | ✅ |

---

## Next Topic

```txt
Day 23: Medium Mixed Array Practice Part 2
```
