# 01. How to Approach Array Problems

Many beginners directly start writing code after reading the problem.

That is the biggest mistake.

Before coding, always understand:

```txt
What is given?
What is asked?
Which pattern can solve it?
What is the best possible complexity?
```

Array problems are not solved by memorizing code.  
They are solved by identifying the correct pattern.

---

## Step-by-Step Approach

Use this flow for every array problem.

```txt
Read Problem
↓
Understand Input & Output
↓
Check Constraints
↓
Think Brute Force
↓
Identify Pattern
↓
Dry Run
↓
Write Code
↓
Check Edge Cases
↓
Analyze Complexity
```

---

## Step 1: Understand the Problem

Ask:

```txt
What is the input?
What is the output?
Do I need to return value, index, count, or modified array?
```

Example:

```txt
Input: nums = [1, 2, 3, 4]
Output: 10
```

Question is asking for:

```txt
sum of all elements
```

So we need to traverse the array.

---

## Step 2: Check Constraints

Constraints help us decide whether brute force is acceptable or not.

| Constraint | Usually Think |
|---|---|
| `n <= 100` | O(n²) may work |
| `n <= 1000` | O(n²) may work |
| `n <= 10⁵` | O(n) or O(n log n) |
| `n <= 10⁶` | O(n) preferred |

Example:

```txt
n <= 10⁵
```

Avoid unnecessary nested loops.

---

## Step 3: Think Brute Force First

Brute force means the simplest possible solution.

Example:

```txt
Find if duplicate exists.
```

Brute force idea:

```txt
Compare every element with every other element.
```

This usually uses nested loops:

```txt
O(n²)
```

Brute force helps you understand the problem, even if it is not optimal.

---

## Step 4: Try to Optimize

After brute force, ask:

```txt
Can I avoid repeated work?
Can I store something?
Can sorting help?
Can two pointers help?
Can prefix sum help?
Can HashSet or HashMap help?
```

Example:

```txt
Find duplicate element
```

Better idea:

```txt
Use HashSet to store visited elements.
```

Time:

```txt
O(n)
```

---

## Step 5: Identify the Pattern

Most array problems belong to some common pattern.

| Problem Type | Pattern |
|---|---|
| Find sum, max, min, count | Traversal |
| Search an element | Linear Search |
| Search in sorted array | Binary Search |
| Find pair in sorted array | Two Pointers |
| Remove elements in-place | In-place Overwrite |
| Find duplicates | HashSet |
| Count frequency | HashMap |
| Subarray of size `k` | Sliding Window |
| Range sum | Prefix Sum |
| Maximum subarray sum | Kadane’s Algorithm |

---

## Step 6: Dry Run Before Code

Dry run means manually checking how your logic works.

Example:

```txt
nums = [2, 4, 6]
sum = 0
```

| Step | Element | Sum |
|---|---:|---:|
| 1 | 2 | 2 |
| 2 | 4 | 6 |
| 3 | 6 | 12 |

Final answer:

```txt
12
```

---

## Step 7: Check Edge Cases

Always test edge cases.

| Edge Case | Example |
|---|---|
| Single element | `[5]` |
| Empty array if allowed | `[]` |
| All same elements | `[2, 2, 2]` |
| Negative numbers | `[-5, -2, -9]` |
| Already sorted | `[1, 2, 3]` |
| Reverse sorted | `[5, 4, 3]` |
| Target not found | `target = 10` |

---

## Step 8: Analyze Complexity

After writing code, always mention:

```txt
Time Complexity
Space Complexity
```

Example:

```java
for (int i = 0; i < nums.length; i++) {
    sum += nums[i];
}
```

Time:

```txt
O(n)
```

Space:

```txt
O(1)
```

---

## Complete Beginner Template

Use this checklist before solving any array problem:

```txt
1. What is given?
2. What is asked?
3. Do I need index, value, count, sum, or modified array?
4. Is the array sorted?
5. Are duplicates important?
6. Is it about subarray or pair?
7. Can brute force work?
8. Can I optimize using a pattern?
9. What are the edge cases?
10. What is the time and space complexity?
```

---

## Quick Summary

```txt
Understand first.
Think brute force.
Find the pattern.
Dry run.
Then code.
```

Do not directly jump to coding.
