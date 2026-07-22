# Matrix Templates in Java

This file contains reusable Java templates for Matrix and 2D Array problems.

Use these templates when the problem gives:

```txt
int[][]
matrix
grid
rows and columns
spiral order
diagonal
transpose
rotate matrix
```

---

# Template 1: Get Rows and Columns

```java
int rows = matrix.length;
int cols = matrix[0].length;
```

---

# Template 2: Row-wise Traversal

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

# Template 3: Column-wise Traversal

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

# Template 4: Sum of All Elements

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

---

# Template 5: Maximum Element in Matrix

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

---

# Template 6: Search Target in Matrix

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

---

# Template 7: Row Sum

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

# Template 8: Column Sum

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

# Template 9: Primary Diagonal Sum

Use for square matrix.

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

# Template 10: Secondary Diagonal Sum

Use for square matrix.

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

# Template 11: Total Diagonal Sum

Use when both diagonals are needed and center should not be double-counted.

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

---

# Template 12: Spiral Matrix

```java
import java.util.ArrayList;
import java.util.List;

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
```

---

# Template 13: Transpose Matrix

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

# Template 14: Rotate Matrix 90 Degrees Clockwise

Use for square matrix.

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

# Template 15: Boundary Check

Use before accessing a cell.

```java
public boolean isValidCell(int row, int col, int rows, int cols) {
    return row >= 0 && row < rows && col >= 0 && col < cols;
}
```

---

# Template 16: Four Direction Movement

```java
int[] dRow = {-1, 1, 0, 0};
int[] dCol = {0, 0, -1, 1};

for (int d = 0; d < 4; d++) {
    int newRow = row + dRow[d];
    int newCol = col + dCol[d];

    if (newRow >= 0 && newRow < rows && newCol >= 0 && newCol < cols) {
        // valid neighbor cell
    }
}
```

---

# Template Selection Table

| Requirement | Template |
|---|---|
| Visit all cells row by row | Row-wise traversal |
| Visit all cells column by column | Column-wise traversal |
| Sum all elements | Matrix sum |
| Find maximum | Max element |
| Find target | Search matrix |
| Sum of every row | Row sum |
| Sum of every column | Column sum |
| Diagonal logic | Diagonal sum |
| Spiral order | Spiral matrix |
| Convert rows to columns | Transpose |
| Rotate square matrix | Transpose + reverse rows |
| Grid movement | Direction arrays |
| Avoid invalid index | Boundary check |

---

# Final Array Pattern Selection Table

| Signal in Problem | Pattern to Use |
|---|---|
| Need to scan all elements | Traversal |
| Need to search unsorted array | Linear Search |
| Sorted array + search | Binary Search |
| Pair in sorted array | Two Pointers |
| Remove duplicates/elements in-place | In-place Overwrite |
| Duplicate check | HashSet |
| Count frequency | HashMap |
| Arrange / kth / min difference | Sorting |
| Merge two sorted arrays | Merge Sorted Arrays |
| Subarray of size k | Fixed Sliding Window |
| Longest/smallest subarray condition | Variable Sliding Window |
| Range sum query | Prefix Sum |
| Count subarray sum k | Prefix Sum + HashMap |
| Maximum subarray sum | Kadane |
| Stock prices | Stock Profit |
| One missing / one single | XOR / Math |
| Rotate / sort colors / product except self | Array Manipulation |
| 2D array / grid | Matrix |

---

# Beginner Rule

For matrix problems, always start with:

```java
int rows = matrix.length;
int cols = matrix[0].length;
```

Then decide:

```txt
row-wise
column-wise
diagonal
spiral
grid movement
```
