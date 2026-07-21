# Day 19 Practice: Pattern 17 Rotate, Dutch Flag, Product Except Self, Difference Array

Today's goal is to master four important array manipulation patterns:

```txt
1. Rotate Array
2. Dutch National Flag
3. Product Except Self
4. Difference Array
```

---

## Practice Method

For every problem, write:

```txt
Given:
Asked:
Which transformation is needed?
Can it be done in-place?
Is extra space allowed?
Pattern:
Return:
Time Complexity:
Space Complexity:
```

Example:

```txt
Problem: Rotate Array

Given: integer array and k
Asked: rotate right by k steps
Which transformation is needed? circular shifting
Can it be done in-place? yes
Is extra space allowed? not needed
Pattern: Rotate Array using Reverse
Return: modified array
Time: O(n)
Space: O(1)
```

---

# Manual Practice Problems

## 1. Rotate Array Right

```txt
Input:
nums = [1, 2, 3, 4, 5, 6, 7]
k = 3

Output:
[5, 6, 7, 1, 2, 3, 4]
```

Think:

```txt
Reverse full array.
Reverse first k.
Reverse remaining part.
```

---

## 2. Rotate Array Left

```txt
Input:
nums = [1, 2, 3, 4, 5]
k = 2

Output:
[3, 4, 5, 1, 2]
```

Think:

```txt
Reverse first k.
Reverse remaining part.
Reverse full array.
```

---

## 3. Rotate With Large K

```txt
Input:
nums = [1, 2, 3, 4, 5]
k = 7

Output:
[4, 5, 1, 2, 3]
```

Why?

```txt
k = 7 % 5 = 2
```

---

## 4. Sort Colors

```txt
Input:
nums = [2, 0, 2, 1, 1, 0]

Output:
[0, 0, 1, 1, 2, 2]
```

Think:

```txt
Use low, mid, high.
```

---

## 5. Sort 0s and 1s

```txt
Input:
nums = [1, 0, 1, 0, 0, 1]

Output:
[0, 0, 0, 1, 1, 1]
```

Think:

```txt
Use two pointers or counting.
```

---

## 6. Product Except Self

```txt
Input:
nums = [1, 2, 3, 4]

Output:
[24, 12, 8, 6]
```

Think:

```txt
answer[i] = left product * right product
```

---

## 7. Product Except Self With Zero

```txt
Input:
nums = [1, 2, 0, 4]

Output:
[0, 0, 8, 0]
```

Think:

```txt
Prefix-suffix method handles zero safely.
```

---

## 8. Difference Array Range Update

```txt
Input:
n = 5

updates = [
  [1, 3, 2],
  [2, 4, 3]
]

Output:
[0, 2, 5, 5, 3]
```

Think:

```txt
diff[left] += value
diff[right + 1] -= value
```

---

# Dry Run Practice 1: Rotate Array

Dry run:

```txt
nums = [1, 2, 3, 4, 5, 6, 7]
k = 3
```

Fill this:

| Step | Operation | Array |
|---:|---|---|
| 1 | Original |  |
| 2 | Reverse full array |  |
| 3 | Reverse first k elements |  |
| 4 | Reverse remaining elements |  |

---

## Completed Dry Run Answer

```txt
nums = [1, 2, 3, 4, 5, 6, 7]
k = 3
```

| Step | Operation | Array |
|---:|---|---|
| 1 | Original | [1, 2, 3, 4, 5, 6, 7] |
| 2 | Reverse full array | [7, 6, 5, 4, 3, 2, 1] |
| 3 | Reverse first k elements | [5, 6, 7, 4, 3, 2, 1] |
| 4 | Reverse remaining elements | [5, 6, 7, 1, 2, 3, 4] |

Answer:

```txt
[5, 6, 7, 1, 2, 3, 4]
```

---

# Dry Run Practice 2: Dutch National Flag

Dry run:

```txt
nums = [2, 0, 2, 1, 1, 0]
```

Fill this table:

| Step | low | mid | high | nums[mid] | Action | Array |
|---:|---:|---:|---:|---:|---|---|
| 1 |  |  |  |  |  |  |
| 2 |  |  |  |  |  |  |
| 3 |  |  |  |  |  |  |
| 4 |  |  |  |  |  |  |
| 5 |  |  |  |  |  |  |
| 6 |  |  |  |  |  |  |

---

## Completed Dutch Flag Dry Run

```txt
nums = [2, 0, 2, 1, 1, 0]
```

| Step | low | mid | high | nums[mid] | Action | Array |
|---:|---:|---:|---:|---:|---|---|
| 1 | 0 | 0 | 5 | 2 | swap mid and high, high-- | [0, 0, 2, 1, 1, 2] |
| 2 | 0 | 0 | 4 | 0 | swap low and mid, low++, mid++ | [0, 0, 2, 1, 1, 2] |
| 3 | 1 | 1 | 4 | 0 | swap low and mid, low++, mid++ | [0, 0, 2, 1, 1, 2] |
| 4 | 2 | 2 | 4 | 2 | swap mid and high, high-- | [0, 0, 1, 1, 2, 2] |
| 5 | 2 | 2 | 3 | 1 | mid++ | [0, 0, 1, 1, 2, 2] |
| 6 | 2 | 3 | 3 | 1 | mid++ | [0, 0, 1, 1, 2, 2] |

Final:

```txt
[0, 0, 1, 1, 2, 2]
```

---

# Dry Run Practice 3: Product Except Self

Dry run:

```txt
nums = [1, 2, 3, 4]
```

First pass:

| i | prefix before | answer[i] | prefix after |
|---:|---:|---:|---:|
| 0 |  |  |  |
| 1 |  |  |  |
| 2 |  |  |  |
| 3 |  |  |  |

Second pass:

| i | suffix before | answer[i] after multiply | suffix after |
|---:|---:|---:|---:|
| 3 |  |  |  |
| 2 |  |  |  |
| 1 |  |  |  |
| 0 |  |  |  |

---

## Completed Product Except Self Dry Run

```txt
nums = [1, 2, 3, 4]
```

First pass:

| i | prefix before | answer[i] | prefix after |
|---:|---:|---:|---:|
| 0 | 1 | 1 | 1 |
| 1 | 1 | 1 | 2 |
| 2 | 2 | 2 | 6 |
| 3 | 6 | 6 | 24 |

After first pass:

```txt
answer = [1, 1, 2, 6]
```

Second pass:

| i | suffix before | answer[i] after multiply | suffix after |
|---:|---:|---:|---:|
| 3 | 1 | 6 | 4 |
| 2 | 4 | 8 | 12 |
| 1 | 12 | 12 | 24 |
| 0 | 24 | 24 | 24 |

Final:

```txt
[24, 12, 8, 6]
```

---

# Dry Run Practice 4: Difference Array

Dry run:

```txt
n = 5

updates = [
  [1, 3, 2],
  [2, 4, 3]
]
```

Fill this:

| Step | Operation | diff |
|---:|---|---|
| 1 | Initial |  |
| 2 | Apply [1, 3, 2] |  |
| 3 | Apply [2, 4, 3] |  |

Then reconstruct:

| i | result[i] |
|---:|---:|
| 0 |  |
| 1 |  |
| 2 |  |
| 3 |  |
| 4 |  |

---

## Completed Difference Array Dry Run

Initial:

```txt
diff = [0, 0, 0, 0, 0]
```

| Step | Operation | diff |
|---:|---|---|
| 1 | Initial | [0, 0, 0, 0, 0] |
| 2 | Apply [1, 3, 2] | [0, 2, 0, 0, -2] |
| 3 | Apply [2, 4, 3] | [0, 2, 3, 0, -2] |

Reconstruct:

| i | result[i] |
|---:|---:|
| 0 | 0 |
| 1 | 2 |
| 2 | 5 |
| 3 | 5 |
| 4 | 3 |

Final:

```txt
[0, 2, 5, 5, 3]
```

---

# Common Mistake Practice

## Mistake 1

Find the issue:

```java
rotate(nums, k);
```

without:

```java
k = k % nums.length;
```

Problem:

```txt
Large k may cause wrong rotation.
```

Correct:

```java
k = k % nums.length;
```

---

## Mistake 2

Find the issue:

```java
else {
    swap(nums, mid, high);
    high--;
    mid++;
}
```

in Dutch National Flag.

Problem:

```txt
After swapping with high, nums[mid] is unknown.
```

Correct:

```java
else {
    swap(nums, mid, high);
    high--;
}
```

---

## Mistake 3

Find the issue:

```java
int prefix = 0;
```

in Product Except Self.

Problem:

```txt
Multiplication identity should be 1, not 0.
```

Correct:

```java
int prefix = 1;
```

---

## Mistake 4

Find the issue:

```java
diff[right + 1] -= value;
```

without boundary check.

Problem:

```txt
If right is last index, right + 1 is out of bounds.
```

Correct:

```java
if (right + 1 < n) {
    diff[right + 1] -= value;
}
```

---

## Mistake 5

Find the issue:

```txt
Question asks for many range updates.
```

Mistake:

```txt
Updating every element from left to right for every query.
```

Problem:

```txt
This can become O(n × q).
```

Better:

```txt
Use Difference Array.
```

---

# LeetCode Practice

| No. | Problem | Concept |
|---:|---|---|
| 189 | Rotate Array | Reverse method |
| 75 | Sort Colors | Dutch National Flag |
| 238 | Product of Array Except Self | Prefix + suffix product |
| 370 | Range Addition | Difference Array |
| 1109 | Corporate Flight Bookings | Difference Array |
| 1094 | Car Pooling | Difference Array / timeline |
| 283 | Move Zeroes | In-place overwrite |
| 905 | Sort Array By Parity | Partition logic |
| 724 | Find Pivot Index | Prefix logic |
| 1480 | Running Sum of 1d Array | Prefix logic |

---

# Answer Key

| Problem | Pattern | Time | Space |
|---:|---|---:|---:|
| 1 | Rotate Array | O(n) | O(1) |
| 2 | Rotate Array | O(n) | O(1) |
| 3 | Rotate Array | O(n) | O(1) |
| 4 | Dutch National Flag | O(n) | O(1) |
| 5 | Two Pointer Partition | O(n) | O(1) |
| 6 | Product Except Self | O(n) | O(1) extra |
| 7 | Product Except Self | O(n) | O(1) extra |
| 8 | Difference Array | O(n + q) | O(n) |

---

# Before Moving to Pattern 18

You should be able to:

| Skill | Status |
|---|---|
| Rotate array right using reverse | ✅ |
| Rotate array left using reverse | ✅ |
| Handle large `k` using modulo | ✅ |
| Sort 0s, 1s, and 2s using Dutch Flag | ✅ |
| Use `low`, `mid`, and `high` correctly | ✅ |
| Solve Product Except Self without division | ✅ |
| Understand prefix and suffix product | ✅ |
| Apply range updates using Difference Array | ✅ |
| Reconstruct array from Difference Array | ✅ |
| Explain O(n) and O(1) / O(n) space cases | ✅ |

---

# Next Topic

```txt
Pattern 18: Matrix and Final Checklist
```
