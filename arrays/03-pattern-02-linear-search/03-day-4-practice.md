# Day 4 Practice: Pattern 02 Linear Search

Today's goal is to master the **Linear Search Pattern**.

Linear Search is used when we need to find, check, count, or locate a target by checking elements one by one.

---

## Practice Method

For every problem, write:

```txt
Given:
Asked:
Target:
Pattern:
Should I stop early?
Return:
Time Complexity:
Space Complexity:
```

Example:

```txt
Problem: Find index of target

Given: integer array
Asked: index of target
Target: 7
Pattern: Linear Search
Should I stop early? yes
Return: index if found, otherwise -1
Time: O(n)
Space: O(1)
```

---

## Manual Practice Problems

### 1. Find Target Index

```txt
Input: nums = [4, 8, 1, 9], target = 8
Output: 1
```

Think:

```txt
Check each element until target is found.
```

---

### 2. Target Not Found

```txt
Input: nums = [4, 8, 1, 9], target = 5
Output: -1
```

Think:

```txt
If loop ends and target is not found, return -1.
```

---

### 3. Check If Target Exists

```txt
Input: nums = [10, 20, 30], target = 20
Output: true
```

Return type:

```txt
boolean
```

---

### 4. Count Target Occurrences

```txt
Input: nums = [2, 3, 2, 4, 2], target = 2
Output: 3
```

Important:

```txt
Do not stop early.
Check the full array.
```

---

### 5. First Occurrence

```txt
Input: nums = [5, 2, 7, 2, 9], target = 2
Output: 1
```

Think:

```txt
Return immediately when target is first found.
```

---

### 6. Last Occurrence

```txt
Input: nums = [5, 2, 7, 2, 9], target = 2
Output: 3
```

Think:

```txt
Keep updating answer until loop ends.
```

---

### 7. Return All Indexes

```txt
Input: nums = [1, 4, 1, 5, 1], target = 1
Output: [0, 2, 4]
```

Think:

```txt
Store all matching indexes in a list.
```

---

### 8. Search in 2D Array

```txt
Input:
matrix = [
  [1, 2, 3],
  [4, 5, 6]
]

target = 5

Output: true
```

Think:

```txt
Use nested loops.
```

---

### 9. Return 2D Position

```txt
Input:
matrix = [
  [1, 2, 3],
  [4, 5, 6]
]

target = 6

Output: [1, 2]
```

Think:

```txt
Return row and column.
```

---

## Dry Run Practice

Dry run this manually:

```txt
nums = [3, 6, 9, 12]
target = 9
```

Fill the table:

| Step | `i` | `nums[i]` | Check | Result |
|---:|---:|---:|---|---|
| 1 |  |  |  |  |
| 2 |  |  |  |  |
| 3 |  |  |  |  |

Answer:

```txt
index = ?
```

---

## Completed Dry Run Answer

```txt
nums = [3, 6, 9, 12]
target = 9
```

| Step | `i` | `nums[i]` | Check | Result |
|---:|---:|---:|---|---|
| 1 | 0 | 3 | 3 == 9 | false |
| 2 | 1 | 6 | 6 == 9 | false |
| 3 | 2 | 9 | 9 == 9 | true |

Answer:

```txt
index = 2
```

---

## Common Mistake Practice

### Mistake 1

Find the error:

```java
for (int i = 0; i <= nums.length; i++) {
    if (nums[i] == target) {
        return i;
    }
}
```

Problem:

```txt
i <= nums.length causes invalid index.
```

Correct:

```java
i < nums.length
```

---

### Mistake 2

Find the error:

```java
public int search(int[] nums, int target) {
    for (int i = 0; i < nums.length; i++) {
        if (nums[i] == target) {
            return nums[i];
        }
    }

    return -1;
}
```

Problem:

```txt
Question asks for index, but code returns value.
```

Correct:

```java
return i;
```

---

### Mistake 3

Find the error:

```java
public int countTarget(int[] nums, int target) {
    int count = 0;

    for (int i = 0; i < nums.length; i++) {
        if (nums[i] == target) {
            return count++;
        }
    }

    return count;
}
```

Problem:

```txt
It returns immediately after first match.
For count, we must check the full array.
```

Correct:

```java
count++;
```

---

## LeetCode Practice

| No. | Problem | Concept |
|---:|---|---|
| 1295 | Find Numbers with Even Number of Digits | Traversal + condition check |
| 1431 | Kids With the Greatest Number of Candies | Max + search-like comparison |
| 1470 | Shuffle the Array | Indexing + traversal |
| 1512 | Number of Good Pairs | Search pairs using loops |
| 1346 | Check If N and Its Double Exist | Search target relation |
| 1385 | Find the Distance Value Between Two Arrays | Nested linear search |
| 1672 | Richest Customer Wealth | 2D traversal/search mindset |

---

## Answer Key

| Problem | Pattern | Time | Space |
|---:|---|---:|---:|
| 1 | Linear Search | O(n) | O(1) |
| 2 | Linear Search | O(n) | O(1) |
| 3 | Linear Search | O(n) | O(1) |
| 4 | Linear Search | O(n) | O(1) |
| 5 | Linear Search | O(n) | O(1) |
| 6 | Linear Search | O(n) | O(1) |
| 7 | Linear Search | O(n) | O(k) |
| 8 | Linear Search in 2D | O(rows × columns) | O(1) |
| 9 | Linear Search in 2D | O(rows × columns) | O(1) |

`k` means number of matching indexes stored.

---

## Before Moving to Pattern 03

You should be able to:

| Skill | Status |
|---|---|
| Explain Linear Search | ✅ |
| Identify search target problems | ✅ |
| Return index if found | ✅ |
| Return `-1` if not found | ✅ |
| Return true/false | ✅ |
| Count occurrences | ✅ |
| Find first occurrence | ✅ |
| Find last occurrence | ✅ |
| Search in 2D array | ✅ |
| Decide whether to stop early | ✅ |
| Explain O(n) time | ✅ |
| Avoid index mistakes | ✅ |

---

## Next Topic

```txt
Pattern 03: Binary Search
```
