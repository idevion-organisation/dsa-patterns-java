# Day 15 Practice: Pattern 13 Prefix Sum + HashMap

Today's goal is to master the **Prefix Sum + HashMap Pattern**.

This pattern is used when the problem asks about continuous subarrays with exact sum conditions.

---

## Practice Method

For every problem, write:

```txt
Given:
Asked:
Is it about subarray?
Is exact sum required?
Need count, existence, or longest length?
Can negative numbers exist?
What does map store?
Pattern:
Return:
Time Complexity:
Space Complexity:
```

Example:

```txt
Problem: Count subarrays with sum k

Given: integer array and target k
Asked: number of subarrays with sum k
Is it about subarray? yes
Is exact sum required? yes
Need count, existence, or longest length? count
Can negative numbers exist? yes
What does map store? prefix sum frequency
Pattern: Prefix Sum + HashMap
Return: count
Time: O(n) average
Space: O(n)
```

---

## Manual Practice Problems

### 1. Count Subarrays With Sum K

```txt
Input:
nums = [1, 2, 3]
k = 3

Output:
2
```

Valid subarrays:

```txt
[1, 2]
[3]
```

---

### 2. Count With Negative Numbers

```txt
Input:
nums = [1, -1, 1]
k = 1

Output:
3
```

Valid subarrays:

```txt
[1]
[1, -1, 1]
[1]
```

---

### 3. No Subarray With Sum K

```txt
Input:
nums = [1, 2, 3]
k = 7

Output:
0
```

Think:

```txt
No continuous subarray has sum 7.
```

---

### 4. Check If Subarray Sum K Exists

```txt
Input:
nums = [4, 2, -3, 1, 6]
k = 0

Output:
true
```

Think:

```txt
There is a zero-sum subarray.
```

---

### 5. Longest Subarray With Sum K

```txt
Input:
nums = [10, 5, 2, 7, 1, 9]
k = 15

Output:
4
```

Why?

```txt
[5, 2, 7, 1] has sum 15.
```

---

### 6. Count Zero Sum Subarrays

```txt
Input:
nums = [0, 0, 0]

Output:
6
```

All zero-sum subarrays:

```txt
[0] at index 0
[0] at index 1
[0] at index 2
[0, 0] from 0 to 1
[0, 0] from 1 to 2
[0, 0, 0]
```

---

### 7. Longest Equal 0s and 1s

```txt
Input:
nums = [0, 1, 0]

Output:
2
```

Valid subarrays:

```txt
[0, 1]
[1, 0]
```

---

### 8. Count Subarrays Divisible by K

```txt
Input:
nums = [4, 5, 0, -2, -3, 1]
k = 5

Output:
7
```

Think:

```txt
Use prefix sum remainder frequency.
```

---

## Dry Run Practice

Dry run this:

```txt
nums = [1, 2, 3]
k = 3
```

Fill this table:

| i | nums[i] | currentSum | need = currentSum - k | map has need? | count | map |
|---:|---:|---:|---:|---|---:|---|
| 0 |  |  |  |  |  |  |
| 1 |  |  |  |  |  |  |
| 2 |  |  |  |  |  |  |

Initial map:

```txt
{0=1}
```

---

## Completed Dry Run Answer

```txt
nums = [1, 2, 3]
k = 3
```

Initial:

```txt
map = {0=1}
currentSum = 0
count = 0
```

| i | nums[i] | currentSum | need = currentSum - k | map has need? | count | map |
|---:|---:|---:|---:|---|---:|---|
| 0 | 1 | 1 | -2 | No | 0 | {0=1, 1=1} |
| 1 | 2 | 3 | 0 | Yes, 1 time | 1 | {0=1, 1=1, 3=1} |
| 2 | 3 | 6 | 3 | Yes, 1 time | 2 | {0=1, 1=1, 3=1, 6=1} |

Answer:

```txt
2
```

---

## Longest Subarray Dry Run Practice

Dry run:

```txt
nums = [10, 5, 2, 7, 1, 9]
k = 15
```

Fill:

| i | nums[i] | currentSum | need | map has need? | length | maxLength |
|---:|---:|---:|---:|---|---:|---:|
| 0 |  |  |  |  |  |  |
| 1 |  |  |  |  |  |  |
| 2 |  |  |  |  |  |  |
| 3 |  |  |  |  |  |  |
| 4 |  |  |  |  |  |  |
| 5 |  |  |  |  |  |  |

Initial map:

```txt
{0=-1}
```

---

## Completed Longest Subarray Dry Run Answer

```txt
nums = [10, 5, 2, 7, 1, 9]
k = 15
```

| i | nums[i] | currentSum | need | map has need? | length | maxLength |
|---:|---:|---:|---:|---|---:|---:|
| 0 | 10 | 10 | -5 | No | - | 0 |
| 1 | 5 | 15 | 0 | Yes | 2 | 2 |
| 2 | 2 | 17 | 2 | No | - | 2 |
| 3 | 7 | 24 | 9 | No | - | 2 |
| 4 | 1 | 25 | 10 | Yes | 4 | 4 |
| 5 | 9 | 34 | 19 | No | - | 4 |

Answer:

```txt
4
```

Subarray:

```txt
[5, 2, 7, 1]
```

---

## Common Mistake Practice

### Mistake 1

Find the issue:

```java
HashMap<Integer, Integer> map = new HashMap<>();
```

without:

```java
map.put(0, 1);
```

Problem:

```txt
Subarrays starting from index 0 may not be counted.
```

---

### Mistake 2

Find the issue:

```java
map.put(currentSum, map.getOrDefault(currentSum, 0) + 1);
count += map.getOrDefault(currentSum - k, 0);
```

Problem:

```txt
Current prefix is added before counting.
This can incorrectly count current position.
```

Correct order:

```java
count += map.getOrDefault(currentSum - k, 0);
map.put(currentSum, map.getOrDefault(currentSum, 0) + 1);
```

---

### Mistake 3

Find the issue:

```java
map.put(currentSum, i);
```

in longest subarray problem.

Problem:

```txt
This overwrites earlier index and can reduce possible length.
```

Correct:

```java
if (!map.containsKey(currentSum)) {
    map.put(currentSum, i);
}
```

---

### Mistake 4

Find the issue:

```txt
Need count of subarrays with sum k.
```

Mistake:

```txt
Using HashSet.
```

Problem:

```txt
HashSet cannot store frequency of prefix sums.
```

Correct:

```txt
Use HashMap.
```

---

### Mistake 5

Find the issue:

```txt
Question asks for range sum query [left, right].
```

Mistake:

```txt
Using Prefix Sum + HashMap.
```

Better:

```txt
Use simple Prefix Sum array.
```

---

## LeetCode Practice

| No. | Problem | Concept |
|---:|---|---|
| 560 | Subarray Sum Equals K | Prefix sum frequency |
| 525 | Contiguous Array | Equal 0s and 1s |
| 974 | Subarray Sums Divisible by K | Remainder frequency |
| 523 | Continuous Subarray Sum | Prefix remainder |
| 930 | Binary Subarrays With Sum | Count sum k |
| 1248 | Count Number of Nice Subarrays | Prefix count idea |
| 325 | Maximum Size Subarray Sum Equals k | Longest sum k |
| 437 | Path Sum III | Prefix sum idea on tree later |

---

## Answer Key

| Problem | Pattern | Time | Space |
|---:|---|---:|---:|
| 1 | Prefix Sum + HashMap | O(n) average | O(n) |
| 2 | Prefix Sum + HashMap | O(n) average | O(n) |
| 3 | Prefix Sum + HashMap | O(n) average | O(n) |
| 4 | Prefix Sum + HashSet | O(n) average | O(n) |
| 5 | Prefix Sum + HashMap First Index | O(n) average | O(n) |
| 6 | Prefix Sum + HashMap | O(n) average | O(n) |
| 7 | Transform + Prefix Sum + HashMap | O(n) average | O(n) |
| 8 | Prefix Remainder + HashMap | O(n) average | O(k) or O(n) |

---

## Before Moving to Pattern 14

You should be able to:

| Skill | Status |
|---|---|
| Explain Prefix Sum + HashMap | ✅ |
| Identify subarray sum equals k problems | ✅ |
| Use `currentSum - k` formula | ✅ |
| Count subarrays with sum k | ✅ |
| Initialize `map.put(0, 1)` | ✅ |
| Store prefix sum frequency | ✅ |
| Store prefix sum first index for longest length | ✅ |
| Detect zero-sum subarray | ✅ |
| Handle negative numbers | ✅ |
| Know HashSet vs HashMap usage | ✅ |
| Explain O(n) average time | ✅ |

---

## Next Topic

```txt
Pattern 14: Kadane's Algorithm
```
