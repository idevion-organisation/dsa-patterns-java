# Day 5 Practice: Pattern 03 Binary Search

Today's goal is to master the **Binary Search Pattern**.

Binary Search is used when the array is sorted and we need to search efficiently.

---

## Practice Method

For every problem, write:

```txt
Given:
Asked:
Is array sorted?
Target:
Pattern:
Logic:
Return:
Time Complexity:
Space Complexity:
```

Example:

```txt
Problem: Search target in sorted array

Given: sorted integer array
Asked: index of target
Is array sorted? yes
Target: 7
Pattern: Binary Search
Logic: compare target with middle element
Return: index if found, otherwise -1
Time: O(log n)
Space: O(1)
```

---

## Manual Practice Problems

### 1. Search Target

```txt
Input: nums = [1, 3, 5, 7, 9], target = 7
Output: 3
```

Think:

```txt
Sorted array + search target = Binary Search
```

---

### 2. Target Not Found

```txt
Input: nums = [2, 4, 6, 8, 10], target = 5
Output: -1
```

Think:

```txt
If search space ends, return -1.
```

---

### 3. Return True or False

```txt
Input: nums = [10, 20, 30, 40], target = 30
Output: true
```

Return type:

```txt
boolean
```

---

### 4. Search Insert Position

```txt
Input: nums = [1, 3, 5, 6], target = 2
Output: 1
```

Think:

```txt
2 should be inserted at index 1.
```

---

### 5. First Occurrence

```txt
Input: nums = [1, 2, 2, 2, 3], target = 2
Output: 1
```

Think:

```txt
After finding target, search left side.
```

---

### 6. Last Occurrence

```txt
Input: nums = [1, 2, 2, 2, 3], target = 2
Output: 3
```

Think:

```txt
After finding target, search right side.
```

---

### 7. Lower Bound

```txt
Input: nums = [1, 3, 3, 5, 7], target = 3
Output: 1
```

Meaning:

```txt
First index where nums[index] >= target
```

---

### 8. Upper Bound

```txt
Input: nums = [1, 3, 3, 5, 7], target = 3
Output: 3
```

Meaning:

```txt
First index where nums[index] > target
```

---

## Dry Run Practice

Dry run this manually:

```txt
nums = [3, 6, 9, 12, 15, 18]
target = 15
```

Fill this table:

| Step | left | right | mid | nums[mid] | Decision |
|---:|---:|---:|---:|---:|---|
| 1 |  |  |  |  |  |
| 2 |  |  |  |  |  |

Answer:

```txt
index = ?
```

---

## Completed Dry Run Answer

```txt
nums = [3, 6, 9, 12, 15, 18]
target = 15
```

| Step | left | right | mid | nums[mid] | Decision |
|---:|---:|---:|---:|---:|---|
| 1 | 0 | 5 | 2 | 9 | 9 < 15, search right |
| 2 | 3 | 5 | 4 | 15 | target found |

Answer:

```txt
index = 4
```

---

## Common Mistake Practice

### Mistake 1

Find the error:

```java
while (left <= right) {
    int mid = left + (right - left) / 2;

    if (nums[mid] < target) {
        left = mid;
    }
    else {
        right = mid;
    }
}
```

Problem:

```txt
left = mid and right = mid can create an infinite loop.
```

Correct:

```java
left = mid + 1;
right = mid - 1;
```

---

### Mistake 2

Find the error:

```java
if (nums[mid] == target) {
    return nums[mid];
}
```

Problem:

```txt
Question asks for index, but code returns value.
```

Correct:

```java
return mid;
```

---

### Mistake 3

Find the error:

```java
int mid = (left + right) / 2;
```

Problem:

```txt
This can overflow for very large values.
```

Better:

```java
int mid = left + (right - left) / 2;
```

---

## LeetCode Practice

| No. | Problem | Concept |
|---:|---|---|
| 704 | Binary Search | Basic Binary Search |
| 35 | Search Insert Position | Insert position |
| 34 | Find First and Last Position of Element in Sorted Array | First + Last occurrence |
| 69 | Sqrt(x) | Binary Search on answer |
| 278 | First Bad Version | Binary Search on condition |
| 367 | Valid Perfect Square | Binary Search on answer |
| 374 | Guess Number Higher or Lower | Binary Search |
| 744 | Find Smallest Letter Greater Than Target | Upper bound style |

---

## Answer Key

| Problem | Pattern | Time | Space |
|---:|---|---:|---:|
| 1 | Binary Search | O(log n) | O(1) |
| 2 | Binary Search | O(log n) | O(1) |
| 3 | Binary Search | O(log n) | O(1) |
| 4 | Binary Search | O(log n) | O(1) |
| 5 | Binary Search | O(log n) | O(1) |
| 6 | Binary Search | O(log n) | O(1) |
| 7 | Binary Search | O(log n) | O(1) |
| 8 | Binary Search | O(log n) | O(1) |

---

## Before Moving to Pattern 04

You should be able to:

| Skill | Status |
|---|---|
| Explain Binary Search | ✅ |
| Identify sorted array signal | ✅ |
| Write basic Binary Search | ✅ |
| Dry run Binary Search | ✅ |
| Return index if found | ✅ |
| Return `-1` if not found | ✅ |
| Return true/false | ✅ |
| Understand search insert position | ✅ |
| Understand first occurrence | ✅ |
| Understand last occurrence | ✅ |
| Understand lower bound | ✅ |
| Understand upper bound | ✅ |
| Explain O(log n) | ✅ |
| Avoid infinite loop mistakes | ✅ |

---

## Next Topic

```txt
Pattern 04: Two Pointers
```
