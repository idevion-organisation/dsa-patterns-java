# Day 16 Practice: Pattern 14 Kadane's Algorithm

Today's goal is to master **Kadane's Algorithm**.

Kadane's Algorithm is used when the problem asks for the best sum of a continuous subarray.

---

## Practice Method

For every problem, write:

```txt
Given:
Asked:
Is it a subarray?
Is it continuous?
Need maximum or minimum?
Can negative numbers exist?
Pattern:
Return:
Time Complexity:
Space Complexity:
```

Example:

```txt
Problem: Maximum Subarray Sum

Given: integer array
Asked: maximum sum of continuous subarray
Is it a subarray? yes
Is it continuous? yes
Need maximum or minimum? maximum
Can negative numbers exist? yes
Pattern: Kadane's Algorithm
Return: maximum sum
Time: O(n)
Space: O(1)
```

---

## Manual Practice Problems

### 1. Maximum Subarray Sum

```txt
Input:
nums = [-2, 1, -3, 4, -1, 2, 1, -5, 4]

Output:
6
```

Best subarray:

```txt
[4, -1, 2, 1]
```

---

### 2. All Positive Numbers

```txt
Input:
nums = [1, 2, 3, 4]

Output:
10
```

Think:

```txt
Whole array gives maximum sum.
```

---

### 3. All Negative Numbers

```txt
Input:
nums = [-8, -3, -6, -2, -5]

Output:
-2
```

Think:

```txt
Choose the least negative element.
```

---

### 4. Mixed Values

```txt
Input:
nums = [5, -2, 3, -1, 2]

Output:
7
```

Best subarray:

```txt
[5, -2, 3, -1, 2]
```

---

### 5. Maximum Subarray With Indexes

```txt
Input:
nums = [-2, 1, -3, 4, -1, 2, 1, -5, 4]

Output:
sum = 6
start = 3
end = 6
```

Best subarray:

```txt
[4, -1, 2, 1]
```

---

### 6. Minimum Subarray Sum

```txt
Input:
nums = [3, -4, 2, -3, -1, 7, -5]

Output:
-6
```

Best minimum subarray:

```txt
[-4, 2, -3, -1]
```

---

### 7. Maximum Absolute Subarray Sum

```txt
Input:
nums = [1, -3, 2, 3, -4]

Output:
5
```

Why?

```txt
[2, 3] has sum 5
```

---

### 8. Maximum Circular Subarray Sum

```txt
Input:
nums = [5, -3, 5]

Output:
10
```

Why?

```txt
Circular subarray can take last 5 and first 5.
```

---

## Dry Run Practice

Dry run:

```txt
nums = [-2, 1, -3, 4, -1, 2, 1, -5, 4]
```

Fill this table:

| i | nums[i] | currentSum + nums[i] | currentSum | maxSum |
|---:|---:|---:|---:|---:|
| 0 | -2 | - | -2 | -2 |
| 1 |  |  |  |  |
| 2 |  |  |  |  |
| 3 |  |  |  |  |
| 4 |  |  |  |  |
| 5 |  |  |  |  |
| 6 |  |  |  |  |
| 7 |  |  |  |  |
| 8 |  |  |  |  |

---

## Completed Dry Run Answer

```txt
nums = [-2, 1, -3, 4, -1, 2, 1, -5, 4]
```

Initial:

```txt
currentSum = -2
maxSum = -2
```

| i | nums[i] | currentSum + nums[i] | currentSum | maxSum |
|---:|---:|---:|---:|---:|
| 0 | -2 | - | -2 | -2 |
| 1 | 1 | -1 | 1 | 1 |
| 2 | -3 | -2 | -2 | 1 |
| 3 | 4 | 2 | 4 | 4 |
| 4 | -1 | 3 | 3 | 4 |
| 5 | 2 | 5 | 5 | 5 |
| 6 | 1 | 6 | 6 | 6 |
| 7 | -5 | 1 | 1 | 6 |
| 8 | 4 | 5 | 5 | 6 |

Answer:

```txt
6
```

---

## Common Mistake Practice

### Mistake 1

Find the issue:

```java
int currentSum = 0;
int maxSum = 0;
```

Problem:

```txt
This fails when all elements are negative.
```

Correct:

```java
int currentSum = nums[0];
int maxSum = nums[0];
```

---

### Mistake 2

Find the issue:

```txt
Question asks for subsequence maximum sum.
```

Mistake:

```txt
Using Kadane's Algorithm directly.
```

Problem:

```txt
Kadane's Algorithm is for continuous subarray, not subsequence.
```

---

### Mistake 3

Find the issue:

```java
if (currentSum < 0) {
    currentSum = 0;
}

maxSum = Math.max(maxSum, currentSum);
```

Problem:

```txt
Answer is updated after reset.
This can break all-negative cases.
```

Better:

```java
maxSum = Math.max(maxSum, currentSum);

if (currentSum < 0) {
    currentSum = 0;
}
```

---

### Mistake 4

Find the issue:

```txt
Question asks for exact sum k.
```

Mistake:

```txt
Using Kadane's Algorithm.
```

Correct:

```txt
Use Prefix Sum + HashMap.
```

Kadane is for best maximum sum, not exact target sum.

---

### Mistake 5

Find the issue:

```txt
Question asks for maximum sum of subarray of size k.
```

Mistake:

```txt
Using Kadane's Algorithm.
```

Correct:

```txt
Use Fixed Size Sliding Window.
```

---

## LeetCode Practice

| No. | Problem | Concept |
|---:|---|---|
| 53 | Maximum Subarray | Basic Kadane |
| 918 | Maximum Sum Circular Subarray | Circular Kadane |
| 1749 | Maximum Absolute Sum of Any Subarray | Max + Min Kadane |
| 1191 | K-Concatenation Maximum Sum | Advanced Kadane |
| 152 | Maximum Product Subarray | Kadane-style DP |
| 121 | Best Time to Buy and Sell Stock | Similar running minimum idea |
| 1911 | Maximum Alternating Subsequence Sum | Advanced DP style |

---

## Answer Key

| Problem | Pattern | Time | Space |
|---:|---|---:|---:|
| 1 | Kadane's Algorithm | O(n) | O(1) |
| 2 | Kadane's Algorithm | O(n) | O(1) |
| 3 | Kadane's Algorithm | O(n) | O(1) |
| 4 | Kadane's Algorithm | O(n) | O(1) |
| 5 | Kadane With Indexes | O(n) | O(1) |
| 6 | Minimum Kadane | O(n) | O(1) |
| 7 | Max + Min Kadane | O(n) | O(1) |
| 8 | Circular Kadane | O(n) | O(1) |

---

## Before Moving to Pattern 15

You should be able to:

| Skill | Status |
|---|---|
| Explain Kadane's Algorithm | ✅ |
| Identify maximum subarray sum problems | ✅ |
| Understand continuous subarray meaning | ✅ |
| Use `currentSum` and `maxSum` | ✅ |
| Decide continue or start new | ✅ |
| Handle all-negative arrays | ✅ |
| Find maximum subarray sum | ✅ |
| Find minimum subarray sum | ✅ |
| Return start and end indexes | ✅ |
| Explain O(n) time and O(1) space | ✅ |
| Know when not to use Kadane | ✅ |

---

## Next Topic

```txt
Pattern 15: Stock Profit Pattern
```
