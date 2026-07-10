# Day 7 Practice: Pattern 05 In-place Overwrite

Today's goal is to master the **In-place Overwrite Pattern**.

This pattern is used when we need to modify the same array and avoid extra space.

---

## Practice Method

For every problem, write:

```txt
Given:
Asked:
Modify in-place?
What should be kept?
What should be skipped?
Pattern:
Return:
Time Complexity:
Space Complexity:
```

Example:

```txt
Problem: Remove Element

Given: integer array and val
Asked: remove val in-place
Modify in-place? yes
Keep: nums[i] != val
Skip: nums[i] == val
Pattern: In-place Overwrite
Return: new length
Time: O(n)
Space: O(1)
```

---

## Manual Practice Problems

### 1. Remove Element

```txt
Input: nums = [3, 2, 2, 3], val = 3
Output: 2
Valid part: [2, 2]
```

Think:

```txt
Keep elements not equal to val.
```

---

### 2. Remove Element Not Present

```txt
Input: nums = [1, 2, 3], val = 4
Output: 3
Valid part: [1, 2, 3]
```

Think:

```txt
All elements are valid.
```

---

### 3. Remove All Elements

```txt
Input: nums = [5, 5, 5], val = 5
Output: 0
Valid part: []
```

Think:

```txt
No element should be kept.
```

---

### 4. Remove Duplicates from Sorted Array

```txt
Input: nums = [1, 1, 2, 2, 3]
Output: 3
Valid part: [1, 2, 3]
```

Think:

```txt
Keep only first occurrence of every value.
```

---

### 5. Move Zeroes

```txt
Input: nums = [0, 1, 0, 3, 12]
Output: [1, 3, 12, 0, 0]
```

Think:

```txt
Move non-zero values to front.
Fill remaining positions with zero.
```

---

### 6. Keep Even Numbers

```txt
Input: nums = [1, 2, 3, 4, 5, 6]
Output length: 3
Valid part: [2, 4, 6]
```

Think:

```txt
Keep nums[i] % 2 == 0.
```

---

### 7. Keep Positive Numbers

```txt
Input: nums = [-1, 5, 0, 7, -3]
Output length: 2
Valid part: [5, 7]
```

Think:

```txt
Keep nums[i] > 0.
```

---

### 8. Remove Duplicates Allow At Most Twice

```txt
Input: nums = [1, 1, 1, 2, 2, 3]
Output: 5
Valid part: [1, 1, 2, 2, 3]
```

Think:

```txt
Each number can appear at most two times.
```

---

## Dry Run Practice

Dry run this manually:

```txt
nums = [3, 2, 2, 3]
val = 3
```

Fill this table:

| i | nums[i] | Keep? | index before | Action | index after |
|---:|---:|---|---:|---|---:|
| 0 |  |  |  |  |  |
| 1 |  |  |  |  |  |
| 2 |  |  |  |  |  |
| 3 |  |  |  |  |  |

Answer:

```txt
new length = ?
```

---

## Completed Dry Run Answer

```txt
nums = [3, 2, 2, 3]
val = 3
```

| i | nums[i] | Keep? | index before | Action | index after |
|---:|---:|---|---:|---|---:|
| 0 | 3 | No | 0 | skip | 0 |
| 1 | 2 | Yes | 0 | nums[0] = 2 | 1 |
| 2 | 2 | Yes | 1 | nums[1] = 2 | 2 |
| 3 | 3 | No | 2 | skip | 2 |

Answer:

```txt
new length = 2
```

Valid part:

```txt
[2, 2]
```

---

## Common Mistake Practice

### Mistake 1

Find the error:

```java
public int removeElement(int[] nums, int val) {
    int index = 0;

    for (int i = 0; i < nums.length; i++) {
        if (nums[i] != val) {
            nums[index] = nums[i];
        }
    }

    return index;
}
```

Problem:

```txt
index is never increased.
```

Correct:

```java
nums[index] = nums[i];
index++;
```

---

### Mistake 2

Find the error:

```java
public int removeDuplicates(int[] nums) {
    int index = 0;

    for (int i = 1; i < nums.length; i++) {
        if (nums[i] != nums[i - 1]) {
            nums[index] = nums[i];
            index++;
        }
    }

    return index;
}
```

Problem:

```txt
First element is not handled correctly.
```

Correct:

```java
int index = 1;
```

Because first element is already unique.

---

### Mistake 3

Find the error:

```java
public void moveZeroes(int[] nums) {
    int index = 0;

    for (int i = 0; i < nums.length; i++) {
        if (nums[i] != 0) {
            nums[index] = nums[i];
            index++;
        }
    }
}
```

Problem:

```txt
Remaining positions are not filled with zero.
```

Correct:

```java
while (index < nums.length) {
    nums[index] = 0;
    index++;
}
```

---

## LeetCode Practice

| No. | Problem | Concept |
|---:|---|---|
| 27 | Remove Element | In-place overwrite |
| 26 | Remove Duplicates from Sorted Array | Sorted duplicate removal |
| 80 | Remove Duplicates from Sorted Array II | Allow at most twice |
| 283 | Move Zeroes | Keep non-zero + fill zero |
| 905 | Sort Array By Parity | Partition by condition |
| 922 | Sort Array By Parity II | Position-based overwrite/swap |
| 1089 | Duplicate Zeros | In-place shifting logic |

---

## Answer Key

| Problem | Pattern | Time | Space |
|---:|---|---:|---:|
| 1 | In-place Overwrite | O(n) | O(1) |
| 2 | In-place Overwrite | O(n) | O(1) |
| 3 | In-place Overwrite | O(n) | O(1) |
| 4 | In-place Overwrite | O(n) | O(1) |
| 5 | In-place Overwrite | O(n) | O(1) |
| 6 | In-place Overwrite | O(n) | O(1) |
| 7 | In-place Overwrite | O(n) | O(1) |
| 8 | In-place Overwrite | O(n) | O(1) |

---

## Before Moving to Pattern 06

You should be able to:

| Skill | Status |
|---|---|
| Explain in-place overwrite | ✅ |
| Understand `i` reads and `index` writes | ✅ |
| Remove elements in-place | ✅ |
| Return new length | ✅ |
| Remove duplicates from sorted array | ✅ |
| Move zeroes | ✅ |
| Keep elements based on condition | ✅ |
| Know when remaining elements do not matter | ✅ |
| Explain O(n) time and O(1) space | ✅ |
| Avoid using extra array unnecessarily | ✅ |

---

## Next Topic

```txt
Pattern 06: HashSet / Duplicate Detection
```
