# 01. What is an Array?

An array is a collection of elements of the **same data type** stored together.

```java
int[] arr = {10, 20, 30, 40};
```

Here, `arr` stores 4 integer values.

In Java, once an array is created, its size cannot be changed.

---

## Why Do We Use Arrays?

Without array:

```java
int a = 10;
int b = 20;
int c = 30;
```

With array:

```java
int[] arr = {10, 20, 30};
```

Array helps us store multiple values in one variable.

---

## 1D Array

A 1D array stores elements in a single line.

```java
int[] arr = {10, 20, 30, 40};
```

```txt
Index:  0   1   2   3
Value: 10  20  30  40
```

### Important Formulas

| Concept | Formula |
|---|---|
| First index | `0` |
| Last index | `arr.length - 1` |
| Size | `arr.length` |
| Access | `arr[i]` |
| Update | `arr[i] = value` |

Example:

```java
System.out.println(arr[0]); // 10

arr[1] = 50;
System.out.println(arr[1]); // 50
```

Updated array:

```txt
[10, 50, 30, 40]
```

---

## Traversing a 1D Array

Traversal means visiting each element one by one.

```java
for (int i = 0; i < arr.length; i++) {
    System.out.println(arr[i]);
}
```

Enhanced loop:

```java
for (int num : arr) {
    System.out.println(num);
}
```

| Loop Type | Use When |
|---|---|
| Normal `for` loop | Index is needed |
| Enhanced `for` loop | Only value is needed |

---

## 2D Array

A 2D array is an array of arrays. It is used for matrix/grid problems.

```java
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6}
};
```

```txt
Row 0: 1 2 3
Row 1: 4 5 6
```

For beginner DSA problems, we usually use rectangular 2D arrays where every row has the same number of columns.

### Important 2D Formulas

| Concept | Formula |
|---|---|
| Rows | `matrix.length` |
| Columns | `matrix[0].length` |
| Access | `matrix[i][j]` |
| Update | `matrix[i][j] = value` |

Example:

```java
System.out.println(matrix[0][1]); // 2

matrix[1][2] = 9;
```

---

## Traversing a 2D Array

```java
for (int i = 0; i < matrix.length; i++) {
    for (int j = 0; j < matrix[0].length; j++) {
        System.out.print(matrix[i][j] + " ");
    }
    System.out.println();
}
```

Output:

```txt
1 2 3
4 5 6
```

---

## Dry Run: 1D Traversal

```java
int[] arr = {10, 20, 30};
```

| Step | `i` | `arr[i]` | Output |
|---|---:|---:|---:|
| 1 | 0 | 10 | 10 |
| 2 | 1 | 20 | 20 |
| 3 | 2 | 30 | 30 |

Loop stops when:

```txt
i = 3
3 < arr.length
3 < 3 → false
```

---

## Common Mistakes

### 1. Using invalid last index

Wrong:

```java
arr[arr.length]
```

Correct:

```java
arr[arr.length - 1]
```

---

### 2. Using `<= arr.length`

Wrong:

```java
for (int i = 0; i <= arr.length; i++)
```

Correct:

```java
for (int i = 0; i < arr.length; i++)
```

---

### 3. Confusing rows and columns

```java
matrix.length      // rows
matrix[0].length   // columns
```

---

## Quick Summary

| Topic | Key Point |
|---|---|
| 1D array | Linear data |
| 2D array | Row-column data |
| Indexing | Starts from `0` |
| Last index | `length - 1` |
| Traversal | Visit each element |
| Java array size | Fixed after creation |
| Common error | Invalid index |
