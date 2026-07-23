# Day 21 Pattern Identification Test

This file is only for testing pattern recognition.

Try to identify the pattern before checking the answer.

---

# Test Section

## 1. Problem Signal

```txt
Find the maximum element in an array.
```

Pattern:

```txt
?
```

Answer:

```txt
Traversal
```

---

## 2. Problem Signal

```txt
Find target index in an unsorted array.
```

Pattern:

```txt
?
```

Answer:

```txt
Linear Search
```

---

## 3. Problem Signal

```txt
Find target in sorted array.
```

Pattern:

```txt
?
```

Answer:

```txt
Binary Search
```

---

## 4. Problem Signal

```txt
Check if any value appears more than once.
```

Pattern:

```txt
?
```

Answer:

```txt
HashSet
```

---

## 5. Problem Signal

```txt
Count how many times every number appears.
```

Pattern:

```txt
?
```

Answer:

```txt
HashMap Frequency
```

---

## 6. Problem Signal

```txt
Remove all occurrences of val in-place.
```

Pattern:

```txt
?
```

Answer:

```txt
In-place Overwrite
```

---

## 7. Problem Signal

```txt
Array is sorted. Find two numbers whose sum equals target.
```

Pattern:

```txt
?
```

Answer:

```txt
Two Pointers
```

---

## 8. Problem Signal

```txt
Find maximum sum of any subarray of size k.
```

Pattern:

```txt
?
```

Answer:

```txt
Fixed Size Sliding Window
```

---

## 9. Problem Signal

```txt
Find longest subarray whose sum is less than or equal to k.
```

Pattern:

```txt
?
```

Answer:

```txt
Variable Size Sliding Window
```

---

## 10. Problem Signal

```txt
Answer many range sum queries [left, right].
```

Pattern:

```txt
?
```

Answer:

```txt
Prefix Sum
```

---

## 11. Problem Signal

```txt
Count number of subarrays whose sum equals k.
```

Pattern:

```txt
?
```

Answer:

```txt
Prefix Sum + HashMap
```

---

## 12. Problem Signal

```txt
Find maximum sum of a continuous subarray.
```

Pattern:

```txt
?
```

Answer:

```txt
Kadane's Algorithm
```

---

## 13. Problem Signal

```txt
Find maximum profit from stock prices.
```

Pattern:

```txt
?
```

Answer:

```txt
Stock Profit Pattern
```

---

## 14. Problem Signal

```txt
Every number appears twice except one.
```

Pattern:

```txt
?
```

Answer:

```txt
XOR
```

---

## 15. Problem Signal

```txt
Array has numbers from 0 to n and one number is missing.
```

Pattern:

```txt
?
```

Answer:

```txt
Math Formula / XOR
```

---

## 16. Problem Signal

```txt
Rotate array by k steps.
```

Pattern:

```txt
?
```

Answer:

```txt
Rotate Array
```

---

## 17. Problem Signal

```txt
Sort array containing only 0, 1, and 2.
```

Pattern:

```txt
?
```

Answer:

```txt
Dutch National Flag
```

---

## 18. Problem Signal

```txt
Return product of all elements except current index without division.
```

Pattern:

```txt
?
```

Answer:

```txt
Product Except Self
```

---

## 19. Problem Signal

```txt
Many updates of form add value from left to right.
```

Pattern:

```txt
?
```

Answer:

```txt
Difference Array
```

---

## 20. Problem Signal

```txt
Input is a 2D array and all cells need to be visited.
```

Pattern:

```txt
?
```

Answer:

```txt
Matrix Traversal
```

---

# Mixed Confusion Table

Use this table when two patterns feel similar.

| Confusion | Correct Decision |
|---|---|
| Duplicate exists vs frequency count | HashSet for exists, HashMap for count |
| Sorted search vs unsorted search | Binary Search for sorted, Linear Search for unsorted |
| Fixed window vs variable window | Size k given means fixed, longest/smallest condition means variable |
| Prefix Sum vs Sliding Window | Range query means Prefix Sum, moving subarray means Sliding Window |
| Prefix Sum vs Prefix Sum + HashMap | Range `[l, r]` means Prefix Sum, count exact subarray sum means HashMap |
| Kadane vs Sliding Window | Maximum subarray sum means Kadane, size k means Sliding Window |
| Stock Profit vs Sorting | Never sort stock prices because day order matters |
| XOR vs HashMap | XOR only when pair cancellation condition is exact |
| Matrix vs Array | `int[][]` means Matrix Pattern |

---

# Final Day 21 Score Sheet

Give yourself marks:

| Skill | Marks |
|---|---:|
| Identified 15+ patterns correctly | 5 |
| Explained why pattern fits | 5 |
| Wrote complexity correctly | 5 |
| Solved 10+ problems without hint | 5 |
| Dry ran 5 problems manually | 5 |

Total:

```txt
25 marks
```

Score meaning:

| Score | Level |
|---:|---|
| 20-25 | Strong Day 21 |
| 15-19 | Good, revise confusion table |
| 10-14 | Practice more easy mixed questions |
| Below 10 | Revise Days 3 to 20 again |
