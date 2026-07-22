# Pattern 18: Matrix and Final Checklist

Matrix Pattern is used when the problem gives a 2D array.

A matrix is an array of arrays.

It is commonly used for:

```txt
grid problems
2D traversal
row-wise traversal
column-wise traversal
diagonal traversal
spiral traversal
matrix search
transpose
rotate matrix
island/grid style problems
```

This is the final pattern of the Array Pattern Series.

---

## What Is a Matrix?

A matrix is a 2D array.

Example:

```txt
matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
]
```

It has:

```txt
rows = 3
columns = 3
```

In Java:

```java
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
```

---

## Matrix Indexing

Every element is accessed using:

```java
matrix[row][col]
```

Example:

```txt
matrix[0][0] = 1
matrix[0][1] = 2
matrix[1][0] = 4
matrix[2][2] = 9
```

Important:

```txt
row index starts from 0
column index starts from 0
```

---

## Rows and Columns in Java

```java
int rows = matrix.length;
int cols = matrix[0].length;
```

Meaning:

```txt
matrix.length       → number of rows
matrix[0].length    → number of columns
```

---

## Pattern Signal

Think of Matrix Pattern when the question says:

```txt
2D array
matrix
grid
row
column
cell
spiral order
diagonal
island
path
search in matrix
transpose
rotate matrix
```

Most common signal:

```txt
Input is int[][]
```

---

# Part 1: Basic Matrix Traversal

## Row-wise Traversal

Row-wise traversal means:

```txt
visit elements row by row
```

Example:

```txt
1 2 3
4 5 6
7 8 9
```

Output:

```txt
1 2 3 4 5 6 7 8 9
```

Code:

```java
public void rowWiseTraversal(int[][] matrix) {
    int rows = matrix.length;
    int cols = matrix[0].length;

    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            System.out.print(matrix[i][j] + " ");
        }
    }
}
```

---

## Column-wise Traversal

Column-wise traversal means:

```txt
visit elements column by column
```

Example:

```txt
1 2 3
4 5 6
7 8 9
```

Output:

```txt
1 4 7 2 5 8 3 6 9
```

Code:

```java
public void columnWiseTraversal(int[][] matrix) {
    int rows = matrix.length;
    int cols = matrix[0].length;

    for (int j = 0; j < cols; j++) {
        for (int i = 0; i < rows; i++) {
            System.out.print(matrix[i][j] + " ");
        }
    }
}
```

---

## Row-wise vs Column-wise

| Traversal | Outer Loop | Inner Loop |
|---|---|---|
| Row-wise | rows | columns |
| Column-wise | columns | rows |

Row-wise:

```java
for (int i = 0; i < rows; i++) {
    for (int j = 0; j < cols; j++) {
        // matrix[i][j]
    }
}
```

Column-wise:

```java
for (int j = 0; j < cols; j++) {
    for (int i = 0; i < rows; i++) {
        // matrix[i][j]
    }
}
```

---

# Part 2: Sum of Matrix

Problem:

```txt
Find sum of all elements in matrix.
```

Example:

```txt
matrix = [
  [1, 2],
  [3, 4]
]
```

Output:

```txt
10
```

Code:

```java
public int matrixSum(int[][] matrix) {
    int rows = matrix.length;
    int cols = matrix[0].length;

    int sum = 0;

    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            sum += matrix[i][j];
        }
    }

    return sum;
}
```

Time:

```txt
O(rows × cols)
```

Space:

```txt
O(1)
```

---

# Part 3: Maximum Element in Matrix

Problem:

```txt
Find maximum element in matrix.
```

Code:

```java
public int maxElement(int[][] matrix) {
    int rows = matrix.length;
    int cols = matrix[0].length;

    int max = matrix[0][0];

    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            if (matrix[i][j] > max) {
                max = matrix[i][j];
            }
        }
    }

    return max;
}
```

Important:

```txt
Initialize max with matrix[0][0], not 0.
```

Because matrix may contain negative values.

---

# Part 4: Search in Matrix

Problem:

```txt
Return true if target exists in matrix.
```

Code:

```java
public boolean searchMatrix(int[][] matrix, int target) {
    int rows = matrix.length;
    int cols = matrix[0].length;

    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            if (matrix[i][j] == target) {
                return true;
            }
        }
    }

    return false;
}
```

Time:

```txt
O(rows × cols)
```

---

# Part 5: Row Sum and Column Sum

## Row Sum

Problem:

```txt
Find sum of each row.
```

Code:

```java
public int[] rowSum(int[][] matrix) {
    int rows = matrix.length;
    int cols = matrix[0].length;

    int[] answer = new int[rows];

    for (int i = 0; i < rows; i++) {
        int sum = 0;

        for (int j = 0; j < cols; j++) {
            sum += matrix[i][j];
        }

        answer[i] = sum;
    }

    return answer;
}
```

---

## Column Sum

Problem:

```txt
Find sum of each column.
```

Code:

```java
public int[] columnSum(int[][] matrix) {
    int rows = matrix.length;
    int cols = matrix[0].length;

    int[] answer = new int[cols];

    for (int j = 0; j < cols; j++) {
        int sum = 0;

        for (int i = 0; i < rows; i++) {
            sum += matrix[i][j];
        }

        answer[j] = sum;
    }

    return answer;
}
```

---

# Part 6: Diagonal Sum

Diagonal pattern is used mostly in square matrices.

Example:

```txt
matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
]
```

Primary diagonal:

```txt
1, 5, 9
```

Secondary diagonal:

```txt
3, 5, 7
```

---

## Primary Diagonal

Condition:

```txt
row == col
```

Code:

```java
public int primaryDiagonalSum(int[][] matrix) {
    int n = matrix.length;
    int sum = 0;

    for (int i = 0; i < n; i++) {
        sum += matrix[i][i];
    }

    return sum;
}
```

---

## Secondary Diagonal

Condition:

```txt
row + col == n - 1
```

Code:

```java
public int secondaryDiagonalSum(int[][] matrix) {
    int n = matrix.length;
    int sum = 0;

    for (int i = 0; i < n; i++) {
        sum += matrix[i][n - 1 - i];
    }

    return sum;
}
```

---

## Total Diagonal Sum

Problem:

```txt
Find sum of both diagonals.
If center overlaps, count it only once.
```

Code:

```java
public int diagonalSum(int[][] matrix) {
    int n = matrix.length;
    int sum = 0;

    for (int i = 0; i < n; i++) {
        sum += matrix[i][i];

        if (i != n - 1 - i) {
            sum += matrix[i][n - 1 - i];
        }
    }

    return sum;
}
```

Why condition is needed?

```txt
In odd size matrix, center belongs to both diagonals.
It should be counted only once.
```

---

# Part 7: Spiral Matrix

Spiral traversal means visiting matrix elements in spiral order.

Example:

```txt
matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
]
```

Spiral order:

```txt
[1, 2, 3, 6, 9, 8, 7, 4, 5]
```

---

## Spiral Pattern Signal

Think of Spiral Matrix when the question says:

```txt
spiral order
print matrix in spiral
traverse boundary
layer by layer
clockwise traversal
```

---

## Spiral Matrix Boundaries

Use four boundaries:

| Variable | Meaning |
|---|---|
| `top` | first remaining row |
| `bottom` | last remaining row |
| `left` | first remaining column |
| `right` | last remaining column |

Initial values:

```java
int top = 0;
int bottom = matrix.length - 1;
int left = 0;
int right = matrix[0].length - 1;
```

---

## Spiral Traversal Order

```txt
1. left to right on top row
2. top to bottom on right column
3. right to left on bottom row
4. bottom to top on left column
```

After every step, shrink the boundary.

---

## Complete Java Code: Spiral Order

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> answer = new ArrayList<>();

        int top = 0;
        int bottom = matrix.length - 1;
        int left = 0;
        int right = matrix[0].length - 1;

        while (top <= bottom && left <= right) {
            for (int j = left; j <= right; j++) {
                answer.add(matrix[top][j]);
            }
            top++;

            for (int i = top; i <= bottom; i++) {
                answer.add(matrix[i][right]);
            }
            right--;

            if (top <= bottom) {
                for (int j = right; j >= left; j--) {
                    answer.add(matrix[bottom][j]);
                }
                bottom--;
            }

            if (left <= right) {
                for (int i = bottom; i >= top; i--) {
                    answer.add(matrix[i][left]);
                }
                left++;
            }
        }

        return answer;
    }
}
```

---

## Dry Run: Spiral Matrix

```txt
matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
]
```

Initial:

```txt
top = 0
bottom = 2
left = 0
right = 2
```

Steps:

```txt
top row:        1, 2, 3
right column:   6, 9
bottom row:     8, 7
left column:    4
center:         5
```

Answer:

```txt
[1, 2, 3, 6, 9, 8, 7, 4, 5]
```

---

# Part 8: Transpose Matrix

Transpose means converting rows into columns.

Example:

```txt
matrix = [
  [1, 2, 3],
  [4, 5, 6]
]
```

Transpose:

```txt
[
  [1, 4],
  [2, 5],
  [3, 6]
]
```

Code:

```java
public int[][] transpose(int[][] matrix) {
    int rows = matrix.length;
    int cols = matrix[0].length;

    int[][] result = new int[cols][rows];

    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            result[j][i] = matrix[i][j];
        }
    }

    return result;
}
```

---

# Part 9: Rotate Matrix 90 Degrees

For square matrix:

```txt
Rotate matrix 90 degrees clockwise.
```

Example:

```txt
Original:
[
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
]

Rotated:
[
  [7, 4, 1],
  [8, 5, 2],
  [9, 6, 3]
]
```

Logic:

```txt
1. Transpose matrix
2. Reverse each row
```

Code:

```java
public void rotateMatrix(int[][] matrix) {
    int n = matrix.length;

    for (int i = 0; i < n; i++) {
        for (int j = i + 1; j < n; j++) {
            int temp = matrix[i][j];
            matrix[i][j] = matrix[j][i];
            matrix[j][i] = temp;
        }
    }

    for (int i = 0; i < n; i++) {
        reverseRow(matrix[i]);
    }
}

private void reverseRow(int[] row) {
    int left = 0;
    int right = row.length - 1;

    while (left < right) {
        int temp = row[left];
        row[left] = row[right];
        row[right] = temp;

        left++;
        right--;
    }
}
```

---

# Part 10: Grid Direction Arrays

Many matrix/grid problems need movement in four directions.

Directions:

```txt
up, down, left, right
```

Use:

```java
int[] dRow = {-1, 1, 0, 0};
int[] dCol = {0, 0, -1, 1};
```

Meaning:

| Direction | dRow | dCol |
|---|---:|---:|
| Up | -1 | 0 |
| Down | 1 | 0 |
| Left | 0 | -1 |
| Right | 0 | 1 |

This is useful for:

```txt
island problems
flood fill
grid traversal
path checking
connected cells
```

Basic boundary check:

```java
if (newRow >= 0 && newRow < rows && newCol >= 0 && newCol < cols) {
    // valid cell
}
```

---

# Final Array Pattern Checklist

Use this checklist to identify array patterns quickly.

| Problem Signal | Pattern |
|---|---|
| Visit every element | Traversal |
| Find target in unsorted array | Linear Search |
| Find target in sorted array | Binary Search |
| Sorted pair / reverse / both ends | Two Pointers |
| Remove/keep elements in same array | In-place Overwrite |
| Duplicate / seen before | HashSet |
| Frequency / count occurrence | HashMap Frequency |
| Arrange values / kth / min difference | Sorting |
| Combine two sorted arrays | Merge Sorted Arrays |
| Subarray of size k | Fixed Sliding Window |
| Longest/smallest subarray with condition | Variable Sliding Window |
| Many range sum queries | Prefix Sum |
| Count subarrays with sum k | Prefix Sum + HashMap |
| Maximum subarray sum | Kadane's Algorithm |
| Buy and sell stock | Stock Profit |
| One number appears once | XOR |
| One number missing from range | Math Formula / XOR |
| Rotate / sort colors / product except self | Array Manipulation |
| 2D array / grid / spiral | Matrix |

---

# Final Beginner Decision Flow

When you see an array problem, ask:

```txt
1. Is the array sorted?
2. Is the problem asking for search?
3. Is it asking for duplicate or frequency?
4. Is it asking for subarray?
5. Is the subarray size fixed?
6. Is the problem asking for range sum?
7. Is it asking for maximum subarray sum?
8. Is it asking for in-place modification?
9. Is the input 2D?
10. Are there known number properties?
```

Then choose the pattern.

---

## Time and Space Complexity

| Matrix Operation | Time | Space |
|---|---:|---:|
| Row-wise traversal | O(rows × cols) | O(1) |
| Column-wise traversal | O(rows × cols) | O(1) |
| Search matrix | O(rows × cols) | O(1) |
| Row sum | O(rows × cols) | O(rows) |
| Column sum | O(rows × cols) | O(cols) |
| Spiral traversal | O(rows × cols) | O(rows × cols) for answer |
| Transpose | O(rows × cols) | O(rows × cols) |
| Rotate square matrix | O(n²) | O(1) |

---

## Common Mistakes

### 1. Confusing Rows and Columns

Correct:

```java
int rows = matrix.length;
int cols = matrix[0].length;
```

---

### 2. Using Wrong Loop Order

Row-wise:

```java
for rows
    for cols
```

Column-wise:

```java
for cols
    for rows
```

---

### 3. Forgetting Boundary Checks

Before accessing:

```java
matrix[newRow][newCol]
```

check:

```java
newRow >= 0 && newRow < rows && newCol >= 0 && newCol < cols
```

---

### 4. Double Counting Center in Diagonal Sum

For odd-size matrix, center is common in both diagonals.

Use:

```java
if (i != n - 1 - i)
```

---

### 5. Missing Spiral Boundary Conditions

Always check:

```java
if (top <= bottom)
if (left <= right)
```

before bottom row and left column traversal.

---

## Beginner Checklist

Before applying Matrix Pattern, ask:

```txt
1. Is input a 2D array?
2. How many rows and columns are there?
3. Do I need row-wise or column-wise traversal?
4. Do I need diagonal logic?
5. Do I need spiral order?
6. Do I need transpose or rotate?
7. Do I need movement in four directions?
8. Are boundary checks required?
9. Is the matrix square or rectangular?
10. What is the time complexity?
```

---

## Pattern Summary

| Point | Meaning |
|---|---|
| Pattern Name | Matrix and Final Checklist |
| Pattern Number | 18 |
| Used For | 2D arrays and grid problems |
| Main Variables | `rows`, `cols`, `i`, `j` |
| Main Access | `matrix[i][j]` |
| Common Traversal | nested loops |
| Spiral Variables | `top`, `bottom`, `left`, `right` |
| Grid Movement | direction arrays |
| Time | Usually O(rows × cols) |
| Space | Depends on output |

---

## Array Pattern Series Completed

You have now completed the complete Array Pattern Series:

```txt
Pattern 01 → Traversal
Pattern 02 → Linear Search
Pattern 03 → Binary Search
Pattern 04 → Two Pointers
Pattern 05 → In-place Overwrite
Pattern 06 → HashSet
Pattern 07 → HashMap Frequency
Pattern 08 → Sorting-Based Patterns
Pattern 09 → Merge Sorted Arrays
Pattern 10 → Fixed Size Sliding Window
Pattern 11 → Variable Size Sliding Window
Pattern 12 → Prefix Sum
Pattern 13 → Prefix Sum + HashMap
Pattern 14 → Kadane's Algorithm
Pattern 15 → Stock Profit Pattern
Pattern 16 → XOR and Math Formula
Pattern 17 → Rotate, Dutch Flag, Product Except Self, Difference Array
Pattern 18 → Matrix and Final Checklist
```

Next step:

```txt
Start solving mixed array problems and identify patterns without looking at hints.
```
