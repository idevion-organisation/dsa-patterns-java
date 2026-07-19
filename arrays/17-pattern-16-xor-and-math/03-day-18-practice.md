# Day 18 Practice: Pattern 16 XOR and Math Formula

Today's goal is to master the **XOR and Math Formula Pattern**.

This pattern is used when numbers follow a clear property like pairs, missing value, known range, or mathematical count.

---

## Practice Method

For every problem, write:

```txt
Given:
Asked:
Is there a known range?
Do pairs cancel?
Is one number missing?
Is one number appearing once?
Can sum formula help?
Can XOR help?
Pattern:
Return:
Time Complexity:
Space Complexity:
```

Example:

```txt
Problem: Single Number

Given: integer array
Asked: find number appearing once
Is there a known range? no
Do pairs cancel? yes
Is one number missing? no
Is one number appearing once? yes
Can sum formula help? no
Can XOR help? yes
Pattern: XOR
Return: single number
Time: O(n)
Space: O(1)
```

---

## Manual Practice Problems

### 1. Single Number

```txt
Input:
nums = [2, 2, 1]

Output:
1
```

Think:

```txt
2 cancels with 2.
1 remains.
```

---

### 2. Single Number With More Values

```txt
Input:
nums = [4, 1, 2, 1, 2]

Output:
4
```

Think:

```txt
1 and 2 cancel.
4 remains.
```

---

### 3. Missing Number Using Formula

```txt
Input:
nums = [3, 0, 1]

Output:
2
```

Range:

```txt
0 to 3
```

Expected sum:

```txt
0 + 1 + 2 + 3 = 6
```

Actual sum:

```txt
3 + 0 + 1 = 4
```

Missing:

```txt
2
```

---

### 4. Missing Number Using XOR

```txt
Input:
nums = [0, 1]

Output:
2
```

Range:

```txt
0 to 2
```

Think:

```txt
0 and 1 cancel with array values.
2 remains.
```

---

### 5. Duplicate and Missing

```txt
Input:
nums = [1, 2, 2, 4]

Output:
duplicate = 2
missing = 3
```

Think:

```txt
Use frequency array for beginner-safe solution.
```

---

### 6. Count Good Pairs

```txt
Input:
nums = [1, 2, 3, 1, 1, 3]

Output:
4
```

Why?

```txt
1 appears 3 times → 3 pairs
3 appears 2 times → 1 pair
Total = 4
```

---

### 7. Power of Two

```txt
Input:
n = 16

Output:
true
```

Think:

```txt
16 has only one set bit.
```

---

### 8. Identify Pattern

Identify the best pattern:

```txt
A. Every element appears twice except one
B. Array has numbers from 0 to n and one is missing
C. Need count of frequency of every value
D. Need maximum subarray sum
```

Answer:

```txt
A → XOR
B → Math Formula or XOR
C → HashMap Frequency
D → Kadane's Algorithm
```

---

## Dry Run Practice: Single Number

Dry run:

```txt
nums = [4, 1, 2, 1, 2]
```

Fill this table:

| i | nums[i] | xor before | Operation | xor after |
|---:|---:|---:|---|---:|
| 0 |  |  |  |  |
| 1 |  |  |  |  |
| 2 |  |  |  |  |
| 3 |  |  |  |  |
| 4 |  |  |  |  |

---

## Completed Dry Run Answer

```txt
nums = [4, 1, 2, 1, 2]
```

| i | nums[i] | xor before | Operation | xor after |
|---:|---:|---:|---|---:|
| 0 | 4 | 0 | 0 ^ 4 | 4 |
| 1 | 1 | 4 | 4 ^ 1 | 5 |
| 2 | 2 | 5 | 5 ^ 2 | 7 |
| 3 | 1 | 7 | 7 ^ 1 | 6 |
| 4 | 2 | 6 | 6 ^ 2 | 4 |

Answer:

```txt
4
```

Shortcut understanding:

```txt
4 ^ 1 ^ 2 ^ 1 ^ 2
= 4 ^ (1 ^ 1) ^ (2 ^ 2)
= 4
```

---

## Dry Run Practice: Missing Number Formula

Dry run:

```txt
nums = [3, 0, 1]
```

Fill:

```txt
n = ?
expectedSum = n * (n + 1) / 2 = ?
actualSum = ?
missing = ?
```

---

## Completed Answer

```txt
nums = [3, 0, 1]
```

```txt
n = 3
expectedSum = 3 * 4 / 2 = 6
actualSum = 3 + 0 + 1 = 4
missing = 6 - 4 = 2
```

Answer:

```txt
2
```

---

## Common Mistake Practice

### Mistake 1

Find the issue:

```java
int expectedSum = n * (n + 1) / 2;
```

Problem:

```txt
For large n, this can overflow int.
```

Safer:

```java
long expectedSum = (long) n * (n + 1) / 2;
```

---

### Mistake 2

Find the issue:

```txt
Using XOR when every number does not appear exactly twice.
```

Problem:

```txt
XOR cancellation may not produce correct result.
```

Correct:

```txt
Check conditions carefully.
```

---

### Mistake 3

Find the issue:

```txt
Missing number problem has range 0 to n.
```

Mistake:

```txt
Using range 1 to n formula incorrectly.
```

Correct:

```txt
For 0 to n, sum formula is still n * (n + 1) / 2.
```

---

### Mistake 4

Find the issue:

```txt
Question asks frequency of every element.
```

Mistake:

```txt
Using XOR.
```

Correct:

```txt
Use HashMap Frequency.
```

---

### Mistake 5

Find the issue:

```txt
Question asks maximum subarray sum.
```

Mistake:

```txt
Using sum formula.
```

Correct:

```txt
Use Kadane's Algorithm.
```

---

## LeetCode Practice

| No. | Problem | Concept |
|---:|---|---|
| 136 | Single Number | XOR cancellation |
| 268 | Missing Number | Formula / XOR |
| 645 | Set Mismatch | Duplicate and missing |
| 1512 | Number of Good Pairs | Pair formula |
| 231 | Power of Two | Bit logic |
| 389 | Find the Difference | XOR / character difference |
| 1720 | Decode XORed Array | XOR reverse logic |
| 1486 | XOR Operation in an Array | XOR practice |

---

## Answer Key

| Problem | Pattern | Time | Space |
|---:|---|---:|---:|
| 1 | XOR | O(n) | O(1) |
| 2 | XOR | O(n) | O(1) |
| 3 | Math Formula | O(n) | O(1) |
| 4 | XOR | O(n) | O(1) |
| 5 | Frequency Array | O(n) | O(n) |
| 6 | HashMap + Math Formula | O(n) | O(n) |
| 7 | Bit Logic | O(1) | O(1) |
| 8 | Pattern Identification | - | - |

---

## Before Moving to Pattern 17

You should be able to:

| Skill | Status |
|---|---|
| Explain XOR | ✅ |
| Use `^` operator in Java | ✅ |
| Understand `x ^ x = 0` | ✅ |
| Solve Single Number | ✅ |
| Solve Missing Number using formula | ✅ |
| Solve Missing Number using XOR | ✅ |
| Know when XOR conditions are valid | ✅ |
| Use `n * (n + 1) / 2` formula | ✅ |
| Know when to use long | ✅ |
| Count good pairs using formula | ✅ |
| Differentiate XOR, HashMap, Kadane, Prefix Sum | ✅ |

---

## Next Topic

```txt
Pattern 17: Rotate, Dutch Flag, Product Except Self, Difference Array
```
