# Day 10 Practice: Pattern 08 Sorting-Based Patterns

Today's goal is to master **Sorting-Based Array Patterns**.

Sorting is used when arranging the array makes the logic easier.

---

## Practice Method

For every problem, write:

```txt
Given:
Asked:
Can I sort?
Does original index matter?
What does sorting help with?
Pattern:
Return:
Time Complexity:
Space Complexity:
```

Example:

```txt
Problem: Contains Duplicate

Given: integer array
Asked: check if duplicate exists
Can I sort? yes
Does original index matter? no
What does sorting help with? duplicates become adjacent
Pattern: Sorting-Based
Return: true or false
Time: O(n log n)
Space: O(1)
```

---

## Manual Practice Problems

### 1. Contains Duplicate

```txt
Input: nums = [1, 2, 3, 1]
Output: true
```

Think:

```txt
Sort first.
Duplicate values become adjacent.
```

---

### 2. No Duplicate

```txt
Input: nums = [1, 2, 3, 4]
Output: false
```

Think:

```txt
After sorting, no adjacent equal elements.
```

---

### 3. Count Unique Elements

```txt
Input: nums = [4, 1, 2, 1, 2]
Output: 3
```

Unique values:

```txt
1, 2, 4
```

---

### 4. Kth Smallest

```txt
Input: nums = [7, 10, 4, 3, 20, 15], k = 3
Output: 7
```

Think:

```txt
Sort and return nums[k - 1].
```

---

### 5. Kth Largest

```txt
Input: nums = [7, 10, 4, 3, 20, 15], k = 2
Output: 15
```

Think:

```txt
Sort and return nums[nums.length - k].
```

---

### 6. Minimum Difference

```txt
Input: nums = [5, 3, 8, 1]
Output: 2
```

Think:

```txt
After sorting, compare adjacent elements.
```

---

### 7. Pair Sum After Sorting

```txt
Input: nums = [8, 1, 6, 2], target = 10
Output: true
```

Think:

```txt
Sort first.
Then use two pointers.
```

---

### 8. Longest Consecutive Sequence

```txt
Input: nums = [100, 4, 200, 1, 3, 2]
Output: 4
```

Think:

```txt
Sort and count consecutive values.
Skip duplicates.
```

---

### 9. Sort 0s, 1s, and 2s

```txt
Input: nums = [2, 0, 2, 1, 1, 0]
Output: [0, 0, 1, 1, 2, 2]
```

Think:

```txt
Basic approach: Arrays.sort(nums)
Optimized approach comes later.
```

---

### 10. Third Maximum Distinct Number

```txt
Input: nums = [2, 2, 3, 1]
Output: 1
```

Think:

```txt
Sort first.
Scan from right side.
Count distinct values.
```

---

## Dry Run Practice

Dry run duplicate detection:

```txt
nums = [3, 1, 4, 2, 3]
```

After sorting:

```txt
[1, 2, 3, 3, 4]
```

Fill this table:

| i | nums[i - 1] | nums[i] | Same? | Result |
|---:|---:|---:|---|---|
| 1 |  |  |  |  |
| 2 |  |  |  |  |
| 3 |  |  |  |  |
| 4 |  |  |  |  |

---

## Completed Dry Run Answer

```txt
nums = [3, 1, 4, 2, 3]
```

After sorting:

```txt
[1, 2, 3, 3, 4]
```

| i | nums[i - 1] | nums[i] | Same? | Result |
|---:|---:|---:|---|---|
| 1 | 1 | 2 | No | continue |
| 2 | 2 | 3 | No | continue |
| 3 | 3 | 3 | Yes | duplicate found |
| 4 | - | - | - | not needed |

Answer:

```txt
true
```

---

## Common Mistake Practice

### Mistake 1

Find the issue:

```txt
Question asks for original indexes of two numbers.
```

Mistake:

```txt
Sorting the array directly.
```

Problem:

```txt
Original indexes may be lost.
```

Better:

```txt
Use HashMap.
```

---

### Mistake 2

Find the error:

```java
Arrays.sort(nums);
```

Problem:

```txt
Missing import statement.
```

Correct:

```java
import java.util.Arrays;
```

---

### Mistake 3

Find the error:

```java
return nums[k];
```

for kth smallest.

Problem:

```txt
Array indexes start from 0.
```

Correct:

```java
return nums[k - 1];
```

---

### Mistake 4

Find the error:

```java
return nums[k];
```

for kth largest.

Correct:

```java
return nums[nums.length - k];
```

---

### Mistake 5

Find the issue:

```txt
Minimum difference problem
```

Mistake:

```txt
Checking all pairs using nested loops after sorting.
```

Better:

```txt
Compare only adjacent elements after sorting.
```

---

## LeetCode Practice

| No. | Problem | Concept |
|---:|---|---|
| 217 | Contains Duplicate | Sort + adjacent check |
| 414 | Third Maximum Number | Sort + distinct scan |
| 977 | Squares of a Sorted Array | Sorting / two pointers |
| 268 | Missing Number | Sorting / math later |
| 455 | Assign Cookies | Sorting + greedy |
| 561 | Array Partition | Sorting pairs |
| 905 | Sort Array By Parity | Sorting / partition |
| 75 | Sort Colors | Sorting / Dutch Flag later |
| 128 | Longest Consecutive Sequence | Sorting / HashSet |
| 349 | Intersection of Two Arrays | Sorting / HashSet |

---

## Answer Key

| Problem | Pattern | Time | Space |
|---:|---|---:|---:|
| 1 | Sorting-Based | O(n log n) | O(1) |
| 2 | Sorting-Based | O(n log n) | O(1) |
| 3 | Sorting-Based | O(n log n) | O(1) |
| 4 | Sorting-Based | O(n log n) | O(1) |
| 5 | Sorting-Based | O(n log n) | O(1) |
| 6 | Sorting-Based | O(n log n) | O(1) |
| 7 | Sorting + Two Pointers | O(n log n) | O(1) |
| 8 | Sorting-Based | O(n log n) | O(1) |
| 9 | Sorting-Based | O(n log n) | O(1) |
| 10 | Sorting-Based | O(n log n) | O(1) |

---

## Before Moving to Pattern 09

You should be able to:

| Skill | Status |
|---|---|
| Use `Arrays.sort(nums)` | ✅ |
| Understand sorting modifies array | ✅ |
| Identify when sorting helps | ✅ |
| Know when not to sort | ✅ |
| Check duplicates after sorting | ✅ |
| Count unique values after sorting | ✅ |
| Find kth smallest | ✅ |
| Find kth largest | ✅ |
| Find minimum difference | ✅ |
| Use sorting + two pointers | ✅ |
| Explain O(n log n) time | ✅ |

---

## Next Topic

```txt
Pattern 09: Merge Sorted Arrays
```
