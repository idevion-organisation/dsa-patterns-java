# Day 22 Medium Pattern Identification Test

This file is for testing medium-level pattern recognition.

Try to identify the pattern before checking the answer.

---

# Test Section

## 1. Problem Signal

```txt
Sorted array is given. Return index where target exists or should be inserted.
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

## 2. Problem Signal

```txt
Sorted array is given. Find first and last occurrence of target.
```

Pattern:

```txt
?
```

Answer:

```txt
Binary Search Variation
```

---

## 3. Problem Signal

```txt
Two sorted arrays need to be merged in-place.
```

Pattern:

```txt
?
```

Answer:

```txt
Merge Sorted Arrays
```

---

## 4. Problem Signal

```txt
Find all unique triplets whose sum is zero.
```

Pattern:

```txt
?
```

Answer:

```txt
Sorting + Two Pointers
```

---

## 5. Problem Signal

```txt
Find longest sequence of consecutive numbers in unsorted array.
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

## 6. Problem Signal

```txt
Count subarrays whose product is less than k.
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

## 7. Problem Signal

```txt
Find minimum length subarray whose sum is at least target.
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

## 8. Problem Signal

```txt
Find longest subarray with at most k zeroes.
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

## 9. Problem Signal

```txt
Return product of all elements except current index without division.
```

Pattern:

```txt
?
```

Answer:

```txt
Prefix Product + Suffix Product
```

---

## 10. Problem Signal

```txt
Sort array containing only 0, 1, and 2 in-place.
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

## 11. Problem Signal

```txt
Rotate array by k steps in-place.
```

Pattern:

```txt
?
```

Answer:

```txt
Rotate Array using Reverse
```

---

## 12. Problem Signal

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

## 13. Problem Signal

```txt
Find maximum sum of continuous subarray.
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

## 14. Problem Signal

```txt
Many bookings add seats over a range of flights.
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

## 15. Problem Signal

```txt
Return matrix elements in spiral order.
```

Pattern:

```txt
?
```

Answer:

```txt
Matrix Boundary Traversal
```

---

## 16. Problem Signal

```txt
If matrix cell is zero, make its full row and column zero.
```

Pattern:

```txt
?
```

Answer:

```txt
Matrix Marking
```

---

## 17. Problem Signal

```txt
Find index where left sum equals right sum.
```

Pattern:

```txt
?
```

Answer:

```txt
Prefix / Total Sum
```

---

## 18. Problem Signal

```txt
Array contains numbers from 1 to n. One number is duplicated and one is missing.
```

Pattern:

```txt
?
```

Answer:

```txt
Frequency Array
```

---

## 19. Problem Signal

```txt
Stock prices are given and multiple transactions are allowed.
```

Pattern:

```txt
?
```

Answer:

```txt
Stock Profit Multiple Transactions
```

---

## 20. Problem Signal

```txt
Need largest and second largest values in one pass.
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

# Medium Confusion Table

| Confusion | Correct Decision |
|---|---|
| Search Insert vs Linear Search | Sorted array means Binary Search |
| First/Last Occurrence vs Normal Binary Search | Need boundary, so Binary Search variation |
| 2Sum vs 3Sum | 2Sum sorted uses two pointers, 3Sum uses sorting + fixed index + two pointers |
| Longest Consecutive vs Sorting | HashSet gives O(n), sorting gives O(n log n) |
| Product Less Than K vs Subarray Sum K | Product less than K uses sliding window, exact sum k uses Prefix Sum + HashMap |
| Minimum Subarray Sum vs Maximum Subarray Sum | Minimum length with condition uses sliding window, maximum sum uses Kadane |
| Product Except Self vs Prefix Sum | Product problem needs prefix/suffix product, not prefix sum |
| Range Sum vs Range Update | Range sum uses Prefix Sum, range update uses Difference Array |
| Matrix Spiral vs Matrix Traversal | Spiral needs boundary variables, simple traversal uses nested loops |
| Stock I vs Stock II | One transaction uses minPrice, multiple transactions add positive differences |

---

# Day 22 Self-Scoring

| Skill | Marks |
|---|---:|
| Identified 15+ medium patterns correctly | 5 |
| Solved 10+ medium problems | 5 |
| Explained why each pattern fits | 5 |
| Wrote optimized Java solutions | 5 |
| Dry ran at least 5 problems | 5 |

Total:

```txt
25 marks
```

Score meaning:

| Score | Level |
|---:|---|
| 22-25 | Strong medium array foundation |
| 18-21 | Good, revise confusion table |
| 13-17 | Need more mixed practice |
| Below 13 | Revise Days 12 to 20 again |

---

# Day 22 Final Note

Medium problems are usually not hard because of code.

They become hard because pattern identification is mixed.

Your target should be:

```txt
Problem signal → Pattern → Logic → Code → Complexity
```
