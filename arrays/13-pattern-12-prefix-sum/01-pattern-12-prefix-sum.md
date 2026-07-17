# Pattern 12: Prefix Sum

Prefix Sum is an array pattern used when we need to calculate the sum of a range again and again.

It helps us answer range sum questions faster.

Instead of calculating the sum from `l` to `r` every time, we precompute sums once and answer each query in O(1).

---

## What Is Prefix Sum?

Prefix Sum means storing the sum from the start of the array up to each index.

Example:

```txt
nums = [2, 4, 1, 5, 3]
```

Prefix sums:

```txt
index:       0   1   2   3   4
nums:        2   4   1   5   3
prefix:      2   6   7   12  15
```

Meaning:

```txt
prefix[0] = 2
prefix[1] = 2 + 4 = 6
prefix[2] = 2 + 4 + 1 = 7
prefix[3] = 2 + 4 + 1 + 5 = 12
prefix[4] = 2 + 4 + 1 + 5 + 3 = 15
```

---

## Simple Meaning

```txt
Prefix sum at index i = sum of all elements from index 0 to i
```

Formula:

```txt
prefix[i] = nums[0] + nums[1] + nums[2] + ... + nums[i]
```

---

## Why Prefix Sum Is Needed?

Suppose we need sum from index `1` to `3`.

```txt
nums = [2, 4, 1, 5, 3]
```

Range:

```txt
index 1 to 3 → [4, 1, 5]
```

Normal way:

```txt
4 + 1 + 5 = 10
```

If there are many queries, calculating again and again becomes slow.

Example:

```txt
sum(1, 3)
sum(0, 4)
sum(2, 4)
sum(1, 2)
```

Without prefix sum, each query may take O(n).

With prefix sum:

```txt
precompute once → O(n)
each query → O(1)
```

---

## Pattern Signal

Think of Prefix Sum when the question says:

```txt
range sum
sum from l to r
multiple queries
subarray sum
left sum
right sum
sum between indexes
running sum
pivot index
equilibrium index
```

Most common signal:

```txt
Many range sum queries
```

---

## Prefix Sum vs Sliding Window

| Point | Sliding Window | Prefix Sum |
|---|---|---|
| Best for | Continuous window problems | Fast range sum queries |
| Window size | Fixed or variable | Any range `[l, r]` |
| Query type | Usually one pass answer | Multiple sum queries |
| Time | O(n) | O(n) build + O(1) query |
| Example | Max sum of size k | Sum from index l to r |

If the question asks:

```txt
sum of subarray of size k
```

Think:

```txt
Sliding Window
```

If the question asks:

```txt
sum from l to r many times
```

Think:

```txt
Prefix Sum
```

---

## Two Ways to Build Prefix Sum

There are two common styles.

---

## Style 1: Prefix Array of Size n

Example:

```txt
nums = [2, 4, 1, 5, 3]
```

Prefix:

```txt
prefix = [2, 6, 7, 12, 15]
```

Code:

```java
int[] prefix = new int[nums.length];

prefix[0] = nums[0];

for (int i = 1; i < nums.length; i++) {
    prefix[i] = prefix[i - 1] + nums[i];
}
```

Range sum formula:

```txt
sum(l, r) = prefix[r] - prefix[l - 1]
```

But if `l == 0`:

```txt
sum(0, r) = prefix[r]
```

So we need a special condition for `l == 0`.

---

## Style 2: Prefix Array of Size n + 1

This is cleaner and beginner-friendly.

Example:

```txt
nums = [2, 4, 1, 5, 3]
```

Prefix:

```txt
prefix = [0, 2, 6, 7, 12, 15]
```

Here:

```txt
prefix[0] = 0
prefix[1] = sum of nums[0]
prefix[2] = sum of nums[0..1]
prefix[3] = sum of nums[0..2]
```

Code:

```java
int[] prefix = new int[nums.length + 1];

for (int i = 0; i < nums.length; i++) {
    prefix[i + 1] = prefix[i] + nums[i];
}
```

Range sum formula:

```txt
sum(l, r) = prefix[r + 1] - prefix[l]
```

This avoids special handling for `l == 0`.

---

## Recommended Beginner Style

Use this version:

```java
int[] prefix = new int[nums.length + 1];

for (int i = 0; i < nums.length; i++) {
    prefix[i + 1] = prefix[i] + nums[i];
}
```

Because the range sum formula is clean:

```java
prefix[right + 1] - prefix[left]
```

---

## Complete Java Code: Range Sum Query

Problem:

```txt
Given an array nums and many queries [left, right],
return the sum from left to right.
```

Example:

```txt
nums = [2, 4, 1, 5, 3]
query = [1, 3]
```

Output:

```txt
10
```

Because:

```txt
nums[1] + nums[2] + nums[3] = 4 + 1 + 5 = 10
```

Code:

```java
class Solution {
    public int rangeSum(int[] nums, int left, int right) {
        int[] prefix = new int[nums.length + 1];

        for (int i = 0; i < nums.length; i++) {
            prefix[i + 1] = prefix[i] + nums[i];
        }

        return prefix[right + 1] - prefix[left];
    }
}
```

---

## Line-by-Line Explanation

```java
int[] prefix = new int[nums.length + 1];
```

Creates prefix array with one extra space.

The first value is `0`.

---

```java
for (int i = 0; i < nums.length; i++)
```

Traverses the original array.

---

```java
prefix[i + 1] = prefix[i] + nums[i];
```

Builds the running prefix sum.

Example:

```txt
prefix[1] = prefix[0] + nums[0]
prefix[2] = prefix[1] + nums[1]
```

---

```java
return prefix[right + 1] - prefix[left];
```

Returns the sum from index `left` to `right`.

---

## Why `prefix[right + 1] - prefix[left]`?

Example:

```txt
nums = [2, 4, 1, 5, 3]
prefix = [0, 2, 6, 7, 12, 15]
```

Find sum from index `1` to `3`.

Range:

```txt
[4, 1, 5]
```

Formula:

```txt
prefix[3 + 1] - prefix[1]
prefix[4] - prefix[1]
12 - 2 = 10
```

Answer:

```txt
10
```

---

## Dry Run: Build Prefix Sum

```txt
nums = [2, 4, 1, 5, 3]
```

Initial:

```txt
prefix = [0, 0, 0, 0, 0, 0]
```

| i | nums[i] | Formula | prefix |
|---:|---:|---|---|
| 0 | 2 | prefix[1] = prefix[0] + 2 | [0, 2, 0, 0, 0, 0] |
| 1 | 4 | prefix[2] = prefix[1] + 4 | [0, 2, 6, 0, 0, 0] |
| 2 | 1 | prefix[3] = prefix[2] + 1 | [0, 2, 6, 7, 0, 0] |
| 3 | 5 | prefix[4] = prefix[3] + 5 | [0, 2, 6, 7, 12, 0] |
| 4 | 3 | prefix[5] = prefix[4] + 3 | [0, 2, 6, 7, 12, 15] |

Final prefix:

```txt
[0, 2, 6, 7, 12, 15]
```

---

## Dry Run: Range Sum Query

```txt
nums = [2, 4, 1, 5, 3]
prefix = [0, 2, 6, 7, 12, 15]
query = [1, 3]
```

Formula:

```txt
sum = prefix[right + 1] - prefix[left]
sum = prefix[4] - prefix[1]
sum = 12 - 2
sum = 10
```

Answer:

```txt
10
```

---

## Example 1: Running Sum of Array

Problem:

```txt
Return running sum of array.
```

Input:

```txt
nums = [1, 2, 3, 4]
```

Output:

```txt
[1, 3, 6, 10]
```

Code:

```java
public int[] runningSum(int[] nums) {
    int[] result = new int[nums.length];

    result[0] = nums[0];

    for (int i = 1; i < nums.length; i++) {
        result[i] = result[i - 1] + nums[i];
    }

    return result;
}
```

This is the simplest form of prefix sum.

---

## Example 2: Multiple Range Sum Queries

Problem:

```txt
Given nums and queries, return sum for each query.
```

Input:

```txt
nums = [2, 4, 1, 5, 3]

queries = [
  [0, 2],
  [1, 3],
  [2, 4]
]
```

Output:

```txt
[7, 10, 9]
```

Code:

```java
public int[] rangeSumQueries(int[] nums, int[][] queries) {
    int[] prefix = new int[nums.length + 1];

    for (int i = 0; i < nums.length; i++) {
        prefix[i + 1] = prefix[i] + nums[i];
    }

    int[] answer = new int[queries.length];

    for (int i = 0; i < queries.length; i++) {
        int left = queries[i][0];
        int right = queries[i][1];

        answer[i] = prefix[right + 1] - prefix[left];
    }

    return answer;
}
```

---

## Example 3: Left Sum and Right Sum

Problem:

```txt
For every index, find left sum and right sum.
```

Example:

```txt
nums = [1, 7, 3, 6, 5, 6]
```

At index `3`:

```txt
left side = [1, 7, 3] → sum = 11
right side = [5, 6] → sum = 11
```

This index is called:

```txt
pivot index
```

---

## Example 4: Pivot Index

Problem:

```txt
Find index where left sum equals right sum.
```

Input:

```txt
nums = [1, 7, 3, 6, 5, 6]
```

Output:

```txt
3
```

Code:

```java
public int pivotIndex(int[] nums) {
    int totalSum = 0;

    for (int i = 0; i < nums.length; i++) {
        totalSum += nums[i];
    }

    int leftSum = 0;

    for (int i = 0; i < nums.length; i++) {
        int rightSum = totalSum - leftSum - nums[i];

        if (leftSum == rightSum) {
            return i;
        }

        leftSum += nums[i];
    }

    return -1;
}
```

Logic:

```txt
rightSum = totalSum - leftSum - current element
```

---

## Dry Run: Pivot Index

```txt
nums = [1, 7, 3, 6, 5, 6]
totalSum = 28
```

| i | nums[i] | leftSum | rightSum | Same? |
|---:|---:|---:|---:|---|
| 0 | 1 | 0 | 27 | No |
| 1 | 7 | 1 | 20 | No |
| 2 | 3 | 8 | 17 | No |
| 3 | 6 | 11 | 11 | Yes |

Answer:

```txt
3
```

---

## Example 5: Range Sum with Negative Numbers

Prefix Sum works with negative numbers too.

Example:

```txt
nums = [3, -2, 5, -1]
```

Prefix:

```txt
[0, 3, 1, 6, 5]
```

Query:

```txt
sum(1, 3)
```

Range:

```txt
[-2, 5, -1]
```

Formula:

```txt
prefix[4] - prefix[1]
5 - 3 = 2
```

Answer:

```txt
2
```

This is one reason Prefix Sum is powerful.

Sliding Window may fail with negative numbers, but Prefix Sum can still calculate range sums correctly.

---

## Time and Space Complexity

For building prefix sum:

| Operation | Time | Space |
|---|---:|---:|
| Build prefix array | O(n) | O(n) |
| Single range query | O(1) | O(1) |
| q range queries | O(n + q) | O(n) |

Without prefix sum:

```txt
q queries × O(n) each = O(q × n)
```

With prefix sum:

```txt
build once O(n) + each query O(1)
```

---

## Prefix Sum vs Prefix Sum + HashMap

Prefix Sum alone is used for:

```txt
range sum query
running sum
left sum / right sum
pivot index
```

Prefix Sum + HashMap is used for:

```txt
count subarrays with sum k
longest subarray with sum k
subarray sum with negative numbers
```

That will be the next pattern.

---

## Important Note About Large Sums

If array values are very large, sum may exceed `int`.

In that case, use:

```java
long
```

Example:

```java
long[] prefix = new long[nums.length + 1];
```

For beginner problems, `int` is often enough, but always check constraints.

---

## Common Mistakes

### 1. Wrong Range Formula

For prefix size `n + 1`, correct formula is:

```java
prefix[right + 1] - prefix[left]
```

Wrong:

```java
prefix[right] - prefix[left]
```

---

### 2. Confusing Prefix Size n and n + 1

If prefix size is `n`:

```txt
sum(l, r) = prefix[r] - prefix[l - 1]
```

If prefix size is `n + 1`:

```txt
sum(l, r) = prefix[r + 1] - prefix[l]
```

Do not mix both styles.

---

### 3. Forgetting `l == 0` Case in Size n Prefix

If using prefix size `n`, this needs special handling:

```java
if (left == 0) {
    return prefix[right];
}
```

To avoid this, use prefix size `n + 1`.

---

### 4. Using Sliding Window for Multiple Range Queries

If the question gives many queries:

```txt
[l, r]
```

Sliding window is usually not the best.

Use:

```txt
Prefix Sum
```

---

### 5. Ignoring Negative Numbers

Prefix Sum works with negative numbers.

But normal variable sliding window may not.

So for range sum with negatives, Prefix Sum is safer.

---

## Beginner Checklist

Before applying Prefix Sum, ask:

```txt
1. Is the problem asking for range sum?
2. Are there multiple queries?
3. Do I need sum from l to r?
4. Do I need left sum and right sum?
5. Can I precompute prefix sum once?
6. Which prefix style am I using: n or n + 1?
7. What is my range formula?
8. Can sum exceed int?
9. Is this just range sum or subarray sum count?
```

---

## Pattern Summary

| Point | Meaning |
|---|---|
| Pattern Name | Prefix Sum |
| Pattern Number | 12 |
| Used For | Range sum, running sum, pivot index |
| Main Formula | `prefix[i + 1] = prefix[i] + nums[i]` |
| Range Formula | `prefix[right + 1] - prefix[left]` |
| Build Time | O(n) |
| Query Time | O(1) |
| Space | O(n) |
| Works With Negative Numbers | Yes |

---

## Next Pattern

```txt
Pattern 13: Prefix Sum + HashMap
```
