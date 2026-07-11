# Day 8 Practice: Pattern 06 HashSet / Duplicate Detection

Today's goal is to master the **HashSet Pattern**.

HashSet is used when we need to track seen values, unique elements, duplicates, or existence.

---

## Practice Method

For every problem, write:

```txt
Given:
Asked:
Need duplicate / unique / existence?
Does order matter?
Pattern:
HashSet role:
Return:
Time Complexity:
Space Complexity:
```

Example:

```txt
Problem: Contains Duplicate

Given: integer array
Asked: check if duplicate exists
Need duplicate / unique / existence? duplicate
Does order matter? no
Pattern: HashSet
HashSet role: store seen elements
Return: true if duplicate found, otherwise false
Time: O(n) average
Space: O(n)
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
If element already exists in set, duplicate found.
```

---

### 2. No Duplicate

```txt
Input: nums = [1, 2, 3, 4]
Output: false
```

Think:

```txt
Every element is added once.
No repeated value found.
```

---

### 3. Count Unique Elements

```txt
Input: nums = [1, 2, 2, 3, 1]
Output: 3
```

Unique values:

```txt
1, 2, 3
```

---

### 4. First Repeated Value

```txt
Input: nums = [5, 1, 3, 1, 5]
Output: 1
```

Think:

```txt
Scan left to right.
Return first value that is already in set.
```

---

### 5. Intersection of Two Arrays

```txt
Input:
nums1 = [1, 2, 2, 3]
nums2 = [2, 2, 4]

Output: [2]
```

Think:

```txt
Use one set for nums1.
Use another set for unique result.
```

---

### 6. Check Common Element

```txt
Input:
nums1 = [1, 3, 5]
nums2 = [2, 4, 5]

Output: true
```

Think:

```txt
5 exists in both arrays.
```

---

### 7. Missing Number Using HashSet

```txt
Input: nums = [3, 0, 1]
Output: 2
```

Think:

```txt
Store all values.
Check numbers from 0 to n.
```

---

### 8. Longest Consecutive Sequence

```txt
Input: nums = [100, 4, 200, 1, 3, 2]
Output: 4
```

Why?

```txt
1, 2, 3, 4
```

Think:

```txt
Start counting only from numbers that do not have num - 1.
```

---

## Dry Run Practice

Dry run this manually:

```txt
nums = [1, 2, 3, 1]
```

Fill this table:

| Step | i | nums[i] | Already in set? | Action | Set |
|---:|---:|---:|---|---|---|
| 1 |  |  |  |  |  |
| 2 |  |  |  |  |  |
| 3 |  |  |  |  |  |
| 4 |  |  |  |  |  |

Answer:

```txt
true or false?
```

---

## Completed Dry Run Answer

```txt
nums = [1, 2, 3, 1]
```

| Step | i | nums[i] | Already in set? | Action | Set |
|---:|---:|---:|---|---|---|
| 1 | 0 | 1 | No | add 1 | {1} |
| 2 | 1 | 2 | No | add 2 | {1, 2} |
| 3 | 2 | 3 | No | add 3 | {1, 2, 3} |
| 4 | 3 | 1 | Yes | duplicate found | {1, 2, 3} |

Answer:

```txt
true
```

---

## Common Mistake Practice

### Mistake 1

Find the error:

```java
set.add(nums[i]);

if (set.contains(nums[i])) {
    return true;
}
```

Problem:

```txt
After adding, set will always contain nums[i].
```

Correct:

```java
if (set.contains(nums[i])) {
    return true;
}

set.add(nums[i]);
```

---

### Mistake 2

Find the error:

```java
HashSet<Integer> set = new HashSet<>();
```

Problem:

```txt
Missing import statement.
```

Correct:

```java
import java.util.HashSet;
```

---

### Mistake 3

Find the issue:

```java
HashSet<Integer> set = new HashSet<>();
set.add(3);
set.add(1);
set.add(2);

System.out.println(set);
```

Issue:

```txt
HashSet does not guarantee insertion order.
```

Do not depend on output order.

---

### Mistake 4

Find the issue:

```txt
Question asks for frequency of each element.
```

Problem:

```txt
HashSet cannot store frequency.
```

Correct pattern:

```txt
HashMap Frequency
```

---

## LeetCode Practice

| No. | Problem | Concept |
|---:|---|---|
| 217 | Contains Duplicate | Duplicate detection |
| 349 | Intersection of Two Arrays | Unique common elements |
| 202 | Happy Number | Detect repeated state |
| 268 | Missing Number | Existence checking |
| 575 | Distribute Candies | Count unique types |
| 128 | Longest Consecutive Sequence | HashSet sequence check |
| 219 | Contains Duplicate II | HashSet + window idea |
| 645 | Set Mismatch | Duplicate + missing |

---

## Answer Key

| Problem | Pattern | Time | Space |
|---:|---|---:|---:|
| 1 | HashSet | O(n) average | O(n) |
| 2 | HashSet | O(n) average | O(n) |
| 3 | HashSet | O(n) average | O(n) |
| 4 | HashSet | O(n) average | O(n) |
| 5 | HashSet | O(n + m) average | O(n + m) |
| 6 | HashSet | O(n + m) average | O(n) |
| 7 | HashSet | O(n) average | O(n) |
| 8 | HashSet | O(n) average | O(n) |

---

## Before Moving to Pattern 07

You should be able to:

| Skill | Status |
|---|---|
| Explain HashSet | ✅ |
| Use `import java.util.HashSet` | ✅ |
| Use `add()` | ✅ |
| Use `contains()` | ✅ |
| Detect duplicates | ✅ |
| Count unique elements | ✅ |
| Find intersection | ✅ |
| Know HashSet does not preserve order | ✅ |
| Know when HashSet is not enough | ✅ |
| Explain O(n) average time | ✅ |
| Explain O(n) space | ✅ |

---

## Next Topic

```txt
Pattern 07: HashMap Frequency
```
