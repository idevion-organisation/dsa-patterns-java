# Day 3 Practice: Pattern 01 Traversal

Today's goal is to master the **Traversal Pattern**.

Traversal is used when we need to visit every element of an array.

---

## Practice Method

For every problem, write:

```txt
Given:
Asked:
Pattern:
Logic:
Time Complexity:
Space Complexity:
```

Example:

```txt
Problem: Find sum of array

Given: integer array
Asked: total sum
Pattern: Traversal
Logic: visit each element and add it to sum
Time: O(n)
Space: O(1)
```

---

## Manual Practice Problems

### 1. Print All Elements

```txt
Input: [10, 20, 30]
Output: 10 20 30
```

Pattern:

```txt
Traversal
```

---

### 2. Sum of Array

```txt
Input: [1, 2, 3, 4]
Output: 10
```

Pattern:

```txt
Traversal
```

---

### 3. Find Maximum Element

```txt
Input: [5, 9, 2, 11]
Output: 11
```

Pattern:

```txt
Traversal
```

Important:

```java
int max = arr[0];
```

---

### 4. Find Minimum Element

```txt
Input: [8, 3, 10, 2]
Output: 2
```

Pattern:

```txt
Traversal
```

Important:

```java
int min = arr[0];
```

---

### 5. Count Even Numbers

```txt
Input: [2, 5, 8, 9, 10]
Output: 3
```

Condition:

```java
arr[i] % 2 == 0
```

---

### 6. Count Odd Numbers

```txt
Input: [1, 2, 3, 4, 5]
Output: 3
```

Condition:

```java
arr[i] % 2 != 0
```

---

### 7. Count Positive Numbers

```txt
Input: [-2, 5, 0, 7, -1]
Output: 2
```

Condition:

```java
arr[i] > 0
```

---

### 8. Find Average

```txt
Input: [10, 20, 30]
Output: 20.0
```

Formula:

```txt
average = sum / length
```

---

## LeetCode Practice

| No. | Problem | Concept |
|---:|---|---|
| 1480 | Running Sum of 1D Array | Traversal + Sum |
| 1672 | Richest Customer Wealth | 2D Traversal |
| 1295 | Find Numbers with Even Number of Digits | Count + Traversal |
| 1431 | Kids With the Greatest Number of Candies | Max + Traversal |
| 1732 | Find the Highest Altitude | Running Sum |
| 1929 | Concatenation of Array | Basic Traversal |
| 1470 | Shuffle the Array | Indexing + Traversal |

---

## Answer Key

| Problem | Pattern | Time | Space |
|---:|---|---:|---:|
| 1 | Traversal | O(n) | O(1) |
| 2 | Traversal | O(n) | O(1) |
| 3 | Traversal | O(n) | O(1) |
| 4 | Traversal | O(n) | O(1) |
| 5 | Traversal | O(n) | O(1) |
| 6 | Traversal | O(n) | O(1) |
| 7 | Traversal | O(n) | O(1) |
| 8 | Traversal | O(n) | O(1) |

---

## Before Moving to Pattern 02

You should be able to:

| Skill | Status |
|---|---|
| Traverse a 1D array | ✅ |
| Traverse a 2D array | ✅ |
| Find sum | ✅ |
| Find max/min | ✅ |
| Count based on condition | ✅ |
| Calculate average | ✅ |
| Explain O(n) time | ✅ |
| Avoid index mistakes | ✅ |

---

## Next Topic

```txt
Pattern 02: Linear Search
```
