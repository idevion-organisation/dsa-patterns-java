# Day 6 Practice: Pattern 04 Two Pointers

Today's goal is to master the **Two Pointers Pattern**.

Two Pointers is used when two indexes can move smartly to solve a problem faster.

---

## Practice Method

For every problem, write:

```txt
Given:
Asked:
Is array sorted?
Pointer start:
Pointer movement:
Pattern:
Return:
Time Complexity:
Space Complexity:
```

Example:

```txt
Problem: Pair sum exists

Given: sorted integer array
Asked: check if any pair sum equals target
Is array sorted? yes
Pointer start: left = 0, right = n - 1
Pointer movement: move left if sum is small, move right if sum is large
Pattern: Two Pointers
Return: true or false
Time: O(n)
Space: O(1)
```

---

## Manual Practice Problems

### 1. Pair Sum Exists

```txt
Input: nums = [1, 2, 4, 6, 8], target = 10
Output: true
```

Think:

```txt
Sorted array + pair sum = Two Pointers
```

---

### 2. Pair Sum Not Found

```txt
Input: nums = [1, 2, 4, 6, 8], target = 20
Output: false
```

Think:

```txt
Move left while sum is smaller.
Loop ends when left meets right.
```

---

### 3. Return Pair Indexes

```txt
Input: nums = [1, 3, 5, 7, 9], target = 12
Output: [1, 4]
```

Why?

```txt
nums[1] + nums[4] = 3 + 9 = 12
```

---

### 4. Reverse Array

```txt
Input: [1, 2, 3, 4]
Output: [4, 3, 2, 1]
```

Think:

```txt
Swap left and right.
Move both inward.
```

---

### 5. Palindrome Style Array

```txt
Input: [1, 2, 3, 2, 1]
Output: true
```

Think:

```txt
Compare left and right values.
```

---

### 6. Not a Palindrome

```txt
Input: [1, 2, 3, 4]
Output: false
```

Think:

```txt
If nums[left] != nums[right], return false.
```

---

### 7. Squares of Sorted Array

```txt
Input: [-4, -1, 0, 3, 10]
Output: [0, 1, 9, 16, 100]
```

Think:

```txt
Largest square can be from left or right.
Fill answer from the end.
```

---

### 8. Closest Pair Sum

```txt
Input: nums = [1, 2, 5, 8, 12], target = 11
Output: 10
```

Why?

```txt
2 + 8 = 10 is closest to 11.
```

---

## Dry Run Practice

Dry run this manually:

```txt
nums = [1, 2, 4, 6, 8]
target = 10
```

Fill this table:

| Step | left | right | nums[left] | nums[right] | sum | Decision |
|---:|---:|---:|---:|---:|---:|---|
| 1 |  |  |  |  |  |  |
| 2 |  |  |  |  |  |  |

Answer:

```txt
true or false?
```

---

## Completed Dry Run Answer

```txt
nums = [1, 2, 4, 6, 8]
target = 10
```

| Step | left | right | nums[left] | nums[right] | sum | Decision |
|---:|---:|---:|---:|---:|---:|---|
| 1 | 0 | 4 | 1 | 8 | 9 | 9 < 10, move left |
| 2 | 1 | 4 | 2 | 8 | 10 | pair found |

Answer:

```txt
true
```

---

## Common Mistake Practice

### Mistake 1

Find the error:

```java
while (left <= right) {
    int sum = nums[left] + nums[right];

    if (sum == target) {
        return true;
    }
}
```

Problem:

```txt
For pair sum, left <= right may use same element twice.
Also pointers are not moving, so it can cause infinite loop.
```

Correct:

```java
while (left < right)
```

and move pointers inside the loop.

---

### Mistake 2

Find the error:

```java
if (sum < target) {
    right--;
}
else {
    left++;
}
```

Problem:

```txt
Pointer movement is reversed.
```

Correct:

```java
if (sum < target) {
    left++;
}
else {
    right--;
}
```

---

### Mistake 3

Find the error:

```java
return new int[]{nums[left], nums[right]};
```

Problem:

```txt
If question asks for indexes, this returns values.
```

Correct:

```java
return new int[]{left, right};
```

---

## LeetCode Practice

| No. | Problem | Concept |
|---:|---|---|
| 167 | Two Sum II - Input Array Is Sorted | Pair sum |
| 344 | Reverse String | Reverse using two pointers |
| 977 | Squares of a Sorted Array | Two pointers from both ends |
| 125 | Valid Palindrome | Palindrome-style two pointers |
| 11 | Container With Most Water | Two pointers |
| 15 | 3Sum | Sorting + two pointers |
| 16 | 3Sum Closest | Closest pair logic |
| 88 | Merge Sorted Array | Two pointers / merge logic |

---

## Answer Key

| Problem | Pattern | Time | Space |
|---:|---|---:|---:|
| 1 | Two Pointers | O(n) | O(1) |
| 2 | Two Pointers | O(n) | O(1) |
| 3 | Two Pointers | O(n) | O(1) |
| 4 | Two Pointers | O(n) | O(1) |
| 5 | Two Pointers | O(n) | O(1) |
| 6 | Two Pointers | O(n) | O(1) |
| 7 | Two Pointers | O(n) | O(n) |
| 8 | Two Pointers | O(n) | O(1) |

---

## Before Moving to Pattern 05

You should be able to:

| Skill | Status |
|---|---|
| Explain Two Pointers | ✅ |
| Identify sorted pair-sum problems | ✅ |
| Move left/right correctly | ✅ |
| Use `left < right` for pair problems | ✅ |
| Return pair indexes or values correctly | ✅ |
| Reverse an array using two pointers | ✅ |
| Check palindrome-style arrays | ✅ |
| Solve sorted squares | ✅ |
| Explain O(n) time | ✅ |
| Avoid nested loops when possible | ✅ |

---

## Next Topic

```txt
Pattern 05: In-place Overwrite
```
