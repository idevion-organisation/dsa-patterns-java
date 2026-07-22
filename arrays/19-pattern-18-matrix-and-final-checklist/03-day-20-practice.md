# Day 20 Practice: Pattern 18 Matrix and Final Checklist

Today's goal is to master **Matrix Pattern** and revise the complete Array Pattern Series.

This is the final day of the 20-Day Array Pattern Series.

---

## Practice Method

For every matrix problem, write:

```txt
Given:
Asked:
Is input 1D or 2D?
Rows:
Columns:
Traversal needed:
Pattern:
Return:
Time Complexity:
Space Complexity:
```

Example:

```txt
Problem: Matrix Sum

Given: 2D integer matrix
Asked: sum of all elements
Is input 1D or 2D? 2D
Rows: matrix.length
Columns: matrix[0].length
Traversal needed: row-wise traversal
Pattern: Matrix Traversal
Return: total sum
Time: O(rows × cols)
Space: O(1)
```

---

# Manual Practice Problems

## 1. Row-wise Traversal

```txt
Input:
matrix = [
  [1, 2, 3],
  [4, 5, 6]
]

Output:
1 2 3 4 5 6
```

Think:

```txt
Outer loop rows.
Inner loop columns.
```

---

## 2. Column-wise Traversal

```txt
Input:
matrix = [
  [1, 2, 3],
  [4, 5, 6]
]

Output:
1 4 2 5 3 6
```

Think:

```txt
Outer loop columns.
Inner loop rows.
```

---

## 3. Matrix Sum

```txt
Input:
matrix = [
  [1, 2],
  [3, 4]
]

Output:
10
```

---

## 4. Maximum Element

```txt
Input:
matrix = [
  [-5, -2],
  [-9, -1]
]

Output:
-1
```

Important:

```txt
Initialize max with matrix[0][0], not 0.
```

---

## 5. Search Target

```txt
Input:
matrix = [
  [1, 2, 3],
  [4, 5, 6]
]

target = 5

Output:
true
```

---

## 6. Row Sum

```txt
Input:
matrix = [
  [1, 2, 3],
  [4, 5, 6]
]

Output:
[6, 15]
```

---

## 7. Column Sum

```txt
Input:
matrix = [
  [1, 2, 3],
  [4, 5, 6]
]

Output:
[5, 7, 9]
```

---

## 8. Diagonal Sum

```txt
Input:
matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
]

Output:
25
```

Explanation:

```txt
Primary diagonal: 1 + 5 + 9 = 15
Secondary diagonal: 3 + 5 + 7 = 15
Center 5 counted twice, so subtract once.

Final = 25
```

---

## 9. Spiral Matrix

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

---

## 10. Transpose Matrix

```txt
Input:
matrix = [
  [1, 2, 3],
  [4, 5, 6]
]

Output:
[
  [1, 4],
  [2, 5],
  [3, 6]
]
```

---

## 11. Rotate Matrix 90 Degrees

```txt
Input:
matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
]

Output:
[
  [7, 4, 1],
  [8, 5, 2],
  [9, 6, 3]
]
```

Think:

```txt
Transpose.
Reverse every row.
```

---

## 12. Boundary Check

```txt
rows = 3
cols = 4
cell = (2, 3)

Output:
valid
```

Because:

```txt
0 <= row < rows
0 <= col < cols
```

---

# Dry Run Practice 1: Row-wise Traversal

```txt
matrix = [
  [1, 2, 3],
  [4, 5, 6]
]
```

Fill this:

| i | j | matrix[i][j] |
|---:|---:|---:|
| 0 | 0 |  |
| 0 | 1 |  |
| 0 | 2 |  |
| 1 | 0 |  |
| 1 | 1 |  |
| 1 | 2 |  |

---

## Completed Answer

| i | j | matrix[i][j] |
|---:|---:|---:|
| 0 | 0 | 1 |
| 0 | 1 | 2 |
| 0 | 2 | 3 |
| 1 | 0 | 4 |
| 1 | 1 | 5 |
| 1 | 2 | 6 |

Output:

```txt
1 2 3 4 5 6
```

---

# Dry Run Practice 2: Spiral Matrix

```txt
matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
]
```

Fill:

| Step | Direction | Values |
|---:|---|---|
| 1 | Left to right on top row |  |
| 2 | Top to bottom on right column |  |
| 3 | Right to left on bottom row |  |
| 4 | Bottom to top on left column |  |
| 5 | Center |  |

---

## Completed Spiral Dry Run

| Step | Direction | Values |
|---:|---|---|
| 1 | Left to right on top row | 1, 2, 3 |
| 2 | Top to bottom on right column | 6, 9 |
| 3 | Right to left on bottom row | 8, 7 |
| 4 | Bottom to top on left column | 4 |
| 5 | Center | 5 |

Final:

```txt
[1, 2, 3, 6, 9, 8, 7, 4, 5]
```

---

# Dry Run Practice 3: Rotate Matrix

```txt
matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
]
```

Step 1: Transpose

```txt
[
  [1, 4, 7],
  [2, 5, 8],
  [3, 6, 9]
]
```

Step 2: Reverse each row

```txt
[
  [7, 4, 1],
  [8, 5, 2],
  [9, 6, 3]
]
```

Final:

```txt
[
  [7, 4, 1],
  [8, 5, 2],
  [9, 6, 3]
]
```

---

# Common Mistake Practice

## Mistake 1

Find the issue:

```java
int rows = matrix[0].length;
int cols = matrix.length;
```

Problem:

```txt
Rows and columns are swapped.
```

Correct:

```java
int rows = matrix.length;
int cols = matrix[0].length;
```

---

## Mistake 2

Find the issue:

```java
for (int i = 0; i <= rows; i++)
```

Problem:

```txt
Index out of bounds.
```

Correct:

```java
for (int i = 0; i < rows; i++)
```

---

## Mistake 3

Find the issue:

```java
int max = 0;
```

for matrix maximum.

Problem:

```txt
Fails when all elements are negative.
```

Correct:

```java
int max = matrix[0][0];
```

---

## Mistake 4

Find the issue:

```txt
Diagonal sum counts center twice.
```

Correct:

```java
if (i != n - 1 - i) {
    sum += matrix[i][n - 1 - i];
}
```

---

## Mistake 5

Find the issue:

```txt
Accessing neighbor cell without boundary check.
```

Problem:

```txt
Can cause index out of bounds.
```

Correct:

```java
if (newRow >= 0 && newRow < rows && newCol >= 0 && newCol < cols)
```

---

# LeetCode Practice

| No. | Problem | Concept |
|---:|---|---|
| 867 | Transpose Matrix | Transpose |
| 54 | Spiral Matrix | Spiral traversal |
| 59 | Spiral Matrix II | Fill spiral |
| 48 | Rotate Image | Rotate matrix |
| 1572 | Matrix Diagonal Sum | Diagonal logic |
| 1672 | Richest Customer Wealth | Row sum |
| 766 | Toeplitz Matrix | Diagonal property |
| 73 | Set Matrix Zeroes | Matrix marking |
| 200 | Number of Islands | Grid traversal |
| 463 | Island Perimeter | Grid boundary logic |

---

# Answer Key

| Problem | Pattern | Time | Space |
|---:|---|---:|---:|
| 1 | Matrix Traversal | O(rows × cols) | O(1) |
| 2 | Matrix Traversal | O(rows × cols) | O(1) |
| 3 | Matrix Sum | O(rows × cols) | O(1) |
| 4 | Matrix Max | O(rows × cols) | O(1) |
| 5 | Matrix Search | O(rows × cols) | O(1) |
| 6 | Row Sum | O(rows × cols) | O(rows) |
| 7 | Column Sum | O(rows × cols) | O(cols) |
| 8 | Diagonal Sum | O(n) | O(1) |
| 9 | Spiral Matrix | O(rows × cols) | O(rows × cols) |
| 10 | Transpose | O(rows × cols) | O(rows × cols) |
| 11 | Rotate Matrix | O(n²) | O(1) |
| 12 | Boundary Check | O(1) | O(1) |

---

# Final 20-Day Array Pattern Revision

| Day | Topic | Status |
|---:|---|---|
| 1 | What is Array | ✅ Done |
| 2 | How to Approach Array Problems | ✅ Done |
| 3 | Pattern 01: Traversal | ✅ Done |
| 4 | Pattern 02: Linear Search | ✅ Done |
| 5 | Pattern 03: Binary Search | ✅ Done |
| 6 | Pattern 04: Two Pointers | ✅ Done |
| 7 | Pattern 05: In-place Overwrite | ✅ Done |
| 8 | Pattern 06: HashSet | ✅ Done |
| 9 | Pattern 07: HashMap Frequency | ✅ Done |
| 10 | Pattern 08: Sorting-Based Patterns | ✅ Done |
| 11 | Pattern 09: Merge Sorted Arrays | ✅ Done |
| 12 | Pattern 10: Fixed Size Sliding Window | ✅ Done |
| 13 | Pattern 11: Variable Size Sliding Window | ✅ Done |
| 14 | Pattern 12: Prefix Sum | ✅ Done |
| 15 | Pattern 13: Prefix Sum + HashMap | ✅ Done |
| 16 | Pattern 14: Kadane's Algorithm | ✅ Done |
| 17 | Pattern 15: Stock Profit | ✅ Done |
| 18 | Pattern 16: XOR and Math Formula | ✅ Done |
| 19 | Pattern 17: Rotate, Dutch Flag, Product Except Self, Difference Array | ✅ Done |
| 20 | Pattern 18: Matrix and Final Checklist | ✅ Done |

---

# Final Pattern Identification Test

Identify the pattern:

| Problem Statement | Pattern |
|---|---|
| Find maximum number in array | Traversal |
| Find target in unsorted array | Linear Search |
| Find target in sorted array | Binary Search |
| Find pair sum in sorted array | Two Pointers |
| Remove duplicates from sorted array | In-place Overwrite |
| Check duplicate exists | HashSet |
| Count frequency of elements | HashMap |
| Find kth largest | Sorting |
| Merge two sorted arrays | Merge Sorted Arrays |
| Max sum of subarray size k | Fixed Sliding Window |
| Longest subarray with sum <= k | Variable Sliding Window |
| Sum from left to right many times | Prefix Sum |
| Count subarrays with sum k | Prefix Sum + HashMap |
| Maximum subarray sum | Kadane |
| Best time to buy and sell stock | Stock Profit |
| Every element twice except one | XOR |
| Missing number from 0 to n | Math Formula / XOR |
| Sort 0s, 1s, and 2s | Dutch National Flag |
| Product except self | Prefix + Suffix Product |
| Many range updates | Difference Array |
| Spiral order of matrix | Matrix Spiral |

---

# Final Completion Checklist

You are ready for mixed array practice when you can:

| Skill | Status |
|---|---|
| Read constraints and choose complexity | ✅ |
| Identify brute force first | ✅ |
| Improve using pattern | ✅ |
| Explain why pattern fits | ✅ |
| Dry run with example | ✅ |
| Write Java code without memorizing blindly | ✅ |
| Handle edge cases | ✅ |
| Analyze time complexity | ✅ |
| Analyze space complexity | ✅ |
| Compare similar patterns | ✅ |

---

# Next Step After Day 20

Start solving mixed array questions in this order:

```txt
1. Easy pattern identification
2. Easy implementation
3. Medium pattern identification
4. Medium implementation
5. Mixed revision
6. Timed practice
```

Recommended next folder:

```txt
arrays/
└── 20-mixed-array-practice/
    ├── 01-easy-mixed-practice.md
    ├── 02-medium-mixed-practice.md
    └── 03-pattern-identification-test.md
```
