# Day 14 Practice: Pattern 12 Prefix Sum

Today's goal is to master the **Prefix Sum Pattern**.

Prefix Sum is used when we need fast range sum queries, running sums, or left/right sum calculations.

---

## Practice Method

For every problem, write:

```txt
Given:
Asked:
Need range sum?
Are there multiple queries?
Prefix style:
Formula:
Pattern:
Return:
Time Complexity:
Space Complexity:
```

Example:

```txt
Problem: Range Sum Query

Given: integer array and query [left, right]
Asked: sum from left to right
Need range sum? yes
Are there multiple queries? maybe
Prefix style: n + 1 prefix array
Formula: prefix[right + 1] - prefix[left]
Pattern: Prefix Sum
Return: range sum
Time: O(n) build + O(1) query
Space: O(n)
```

---

## Manual Practice Problems

### 1. Build Prefix Sum

```txt
Input:
nums = [2, 4, 1, 5, 3]

Output:
prefix = [0, 2, 6, 7, 12, 15]
```

Think:

```txt
prefix[i + 1] = prefix[i] + nums[i]
```

---

### 2. Range Sum Query

```txt
Input:
nums = [2, 4, 1, 5, 3]
left = 1
right = 3

Output:
10
```

Why?

```txt
nums[1] + nums[2] + nums[3] = 4 + 1 + 5 = 10
```

---

### 3. Range Starting From Zero

```txt
Input:
nums = [2, 4, 1, 5, 3]
left = 0
right = 2

Output:
7
```

Why?

```txt
2 + 4 + 1 = 7
```

Using prefix size `n + 1`, no special case is needed.

---

### 4. Multiple Range Queries

```txt
Input:
nums = [2, 4, 1, 5, 3]

queries = [
  [0, 2],
  [1, 3],
  [2, 4]
]

Output:
[7, 10, 9]
```

Think:

```txt
Build prefix once.
Answer each query in O(1).
```

---

### 5. Running Sum

```txt
Input:
nums = [1, 2, 3, 4]

Output:
[1, 3, 6, 10]
```

Think:

```txt
Each index stores sum from start to current index.
```

---

### 6. Pivot Index

```txt
Input:
nums = [1, 7, 3, 6, 5, 6]

Output:
3
```

Why?

```txt
Left sum of index 3 = 1 + 7 + 3 = 11
Right sum of index 3 = 5 + 6 = 11
```

---

### 7. No Pivot Index

```txt
Input:
nums = [1, 2, 3]

Output:
-1
```

Think:

```txt
No index has equal left and right sum.
```

---

### 8. Left Right Difference

```txt
Input:
nums = [10, 4, 8, 3]

Output:
[15, 1, 11, 22]
```

Explanation:

```txt
index 0: left = 0, right = 4 + 8 + 3 = 15, diff = 15
index 1: left = 10, right = 8 + 3 = 11, diff = 1
index 2: left = 10 + 4 = 14, right = 3, diff = 11
index 3: left = 10 + 4 + 8 = 22, right = 0, diff = 22
```

---

## Dry Run Practice

Build prefix sum manually:

```txt
nums = [2, 4, 1, 5, 3]
```

Fill this table:

| i | nums[i] | Formula | prefix |
|---:|---:|---|---|
| 0 |  |  |  |
| 1 |  |  |  |
| 2 |  |  |  |
| 3 |  |  |  |
| 4 |  |  |  |

Final prefix:

```txt
?
```

---

## Completed Dry Run Answer

```txt
nums = [2, 4, 1, 5, 3]
```

Initial:

```txt
prefix = [0, 0, 0, 0, 0, 0]
```

| i | nums[i] | Formula | prefix |
|---:|---:|---|---|
| 0 | 2 | prefix[1] = prefix[0] + 2 | [0, 2, 0, 0, 0, 0] |
| 1 | 4 | prefix[2] = prefix[1] + 4 | [0, 2, 6, 0, 0, 0] |
| 2 | 1 | prefix[3] = prefix[2] + 1 | [0, 2, 6, 7, 0, 0] |
| 3 | 5 | prefix[4] = prefix[3] + 5 | [0, 2, 6, 7, 12, 0] |
| 4 | 3 | prefix[5] = prefix[4] + 3 | [0, 2, 6, 7, 12, 15] |

Final prefix:

```txt
[0, 2, 6, 7, 12, 15]
```

---

## Query Dry Run Practice

Use:

```txt
prefix = [0, 2, 6, 7, 12, 15]
```

Find:

```txt
sum(1, 3)
```

Fill:

```txt
sum = prefix[right + 1] - prefix[left]
sum = prefix[?] - prefix[?]
sum = ? - ?
answer = ?
```

---

## Completed Query Dry Run Answer

```txt
left = 1
right = 3
```

Formula:

```txt
sum = prefix[right + 1] - prefix[left]
sum = prefix[4] - prefix[1]
sum = 12 - 2
sum = 10
```

Answer:

```txt
10
```

---

## Common Mistake Practice

### Mistake 1

Find the issue:

```java
return prefix[right] - prefix[left];
```

Problem:

```txt
This is wrong for prefix array of size n + 1.
```

Correct:

```java
return prefix[right + 1] - prefix[left];
```

---

### Mistake 2

Find the issue:

```java
int[] prefix = new int[nums.length];

for (int i = 0; i < nums.length; i++) {
    prefix[i + 1] = prefix[i] + nums[i];
}
```

Problem:

```txt
prefix has size n, but code uses i + 1.
This can cause index out of bounds.
```

Correct:

```java
int[] prefix = new int[nums.length + 1];
```

---

### Mistake 3

Find the issue:

```txt
Using prefix size n formula with prefix size n + 1 array.
```

Problem:

```txt
Formulas are different.
```

Correct for size `n + 1`:

```txt
prefix[right + 1] - prefix[left]
```

---

### Mistake 4

Find the issue:

```txt
Question has many [left, right] queries.
```

Mistake:

```txt
Calculating every query using loop from left to right.
```

Better:

```txt
Build prefix once and answer each query in O(1).
```

---

### Mistake 5

Find the issue:

```txt
Array values are very large.
```

Mistake:

```txt
Using int when sum may overflow.
```

Better:

```txt
Use long.
```

---

## LeetCode Practice

| No. | Problem | Concept |
|---:|---|---|
| 1480 | Running Sum of 1d Array | Basic prefix sum |
| 303 | Range Sum Query - Immutable | Prefix sum query |
| 724 | Find Pivot Index | Left sum and right sum |
| 1732 | Find the Highest Altitude | Running prefix sum |
| 2574 | Left and Right Sum Differences | Prefix / total sum |
| 1991 | Find the Middle Index in Array | Pivot index |
| 1588 | Sum of All Odd Length Subarrays | Prefix sum / subarray sum |
| 2389 | Longest Subsequence With Limited Sum | Prefix after sorting |

---

## Answer Key

| Problem | Pattern | Time | Space |
|---:|---|---:|---:|
| 1 | Prefix Sum | O(n) | O(n) |
| 2 | Prefix Sum | O(n) build + O(1) query | O(n) |
| 3 | Prefix Sum | O(n) build + O(1) query | O(n) |
| 4 | Prefix Sum | O(n + q) | O(n) |
| 5 | Running Prefix Sum | O(n) | O(n) |
| 6 | Prefix / Total Sum | O(n) | O(1) |
| 7 | Prefix / Total Sum | O(n) | O(1) |
| 8 | Prefix / Total Sum | O(n) | O(n) |

---

## Before Moving to Pattern 13

You should be able to:

| Skill | Status |
|---|---|
| Explain Prefix Sum | ✅ |
| Build prefix array of size `n + 1` | ✅ |
| Use `prefix[i + 1] = prefix[i] + nums[i]` | ✅ |
| Answer range sum using `prefix[right + 1] - prefix[left]` | ✅ |
| Handle range starting from index 0 | ✅ |
| Answer multiple queries efficiently | ✅ |
| Solve running sum problems | ✅ |
| Solve pivot index problems | ✅ |
| Know when to use `long` | ✅ |
| Explain O(n) build and O(1) query | ✅ |
| Know difference between Prefix Sum and Prefix Sum + HashMap | ✅ |

---

## Next Topic

```txt
Pattern 13: Prefix Sum + HashMap
```
