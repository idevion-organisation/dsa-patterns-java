# Pattern 13: Prefix Sum + HashMap

Prefix Sum + HashMap is an advanced array pattern used when we need to find or count subarrays based on their sum.

It is mainly used for problems like:

```txt
count subarrays with sum k
find if subarray sum equals k
longest subarray with sum k
subarray with sum 0
subarray problems with negative numbers
```

This pattern is very important because normal sliding window may fail when negative numbers are present.

---

## Before This Pattern

You should already know:

```txt
Prefix Sum
HashMap
Subarray meaning
Frequency counting
```

From the previous pattern, we learned:

```txt
prefix sum = sum from start to current index
```

Now we combine Prefix Sum with HashMap to solve harder subarray problems.

---

## What Problem Does This Pattern Solve?

Suppose we are given:

```txt
nums = [1, 2, 3]
k = 3
```

We need to count subarrays whose sum is `3`.

Valid subarrays:

```txt
[1, 2] → 3
[3]    → 3
```

Answer:

```txt
2
```

A brute force solution checks all subarrays and takes:

```txt
O(n²)
```

Prefix Sum + HashMap can solve this in:

```txt
O(n)
```

---

## Important Word: Subarray

A subarray is a continuous part of an array.

Example:

```txt
nums = [1, 2, 3, 4]
```

Valid subarrays:

```txt
[1, 2]
[2, 3, 4]
[3]
```

Invalid:

```txt
[1, 3]
```

Because elements are skipped.

Prefix Sum + HashMap is mostly used for continuous subarray sum problems.

---

## Why Not Sliding Window?

Sliding Window works well when all numbers are positive or non-negative.

But when negative numbers are present, sliding window becomes unreliable.

Example:

```txt
nums = [3, -2, 5]
```

When we add or remove elements, the sum may increase or decrease unpredictably.

So for subarray sum problems with negative numbers, think:

```txt
Prefix Sum + HashMap
```

---

## Pattern Signal

Think of Prefix Sum + HashMap when the question says:

```txt
subarray sum equals k
count subarrays with sum k
longest subarray with sum k
subarray with sum 0
negative numbers are allowed
continuous subarray
number of subarrays
sum exactly equal to target
```

Most common signal:

```txt
Count subarrays with sum k
```

---

## Core Idea

At every index, we calculate current prefix sum.

```txt
currentSum = sum from index 0 to current index
```

Now suppose we want a subarray with sum `k`.

If:

```txt
currentSum - previousPrefixSum = k
```

Then:

```txt
previousPrefixSum = currentSum - k
```

So for every current prefix sum, we check:

```txt
Has currentSum - k appeared before?
```

If yes, then a subarray with sum `k` exists.

---

## Main Formula

```txt
currentSum - oldPrefixSum = k
```

Rearranged:

```txt
oldPrefixSum = currentSum - k
```

In code:

```java
int need = currentSum - k;
```

Then check:

```java
map.containsKey(need)
```

or for counting:

```java
count += map.getOrDefault(need, 0);
```

---

## What Does HashMap Store?

For counting subarrays with sum `k`, HashMap stores:

```txt
prefix sum → frequency
```

Example:

```txt
map.put(prefixSum, how many times this prefixSum appeared)
```

Why frequency?

Because the same prefix sum can appear multiple times.

Each previous prefix sum can create a valid subarray.

---

## Why Add `0 → 1` Initially?

Before starting, we write:

```java
map.put(0, 1);
```

This means:

```txt
prefix sum 0 has appeared once before the array starts
```

This helps count subarrays starting from index `0`.

Example:

```txt
nums = [3]
k = 3
```

At index 0:

```txt
currentSum = 3
need = currentSum - k = 3 - 3 = 0
```

If map already has `0`, then `[3]` is counted.

So this line is very important:

```java
map.put(0, 1);
```

---

## Complete Java Code: Count Subarrays With Sum K

Problem:

```txt
Count number of continuous subarrays whose sum equals k.
```

Input:

```txt
nums = [1, 2, 3]
k = 3
```

Output:

```txt
2
```

Code:

```java
import java.util.HashMap;

class Solution {
    public int subarraySum(int[] nums, int k) {
        HashMap<Integer, Integer> map = new HashMap<>();

        map.put(0, 1);

        int currentSum = 0;
        int count = 0;

        for (int i = 0; i < nums.length; i++) {
            currentSum += nums[i];

            int need = currentSum - k;

            count += map.getOrDefault(need, 0);

            map.put(currentSum, map.getOrDefault(currentSum, 0) + 1);
        }

        return count;
    }
}
```

---

## Line-by-Line Explanation

```java
HashMap<Integer, Integer> map = new HashMap<>();
```

Creates a HashMap to store prefix sum frequencies.

---

```java
map.put(0, 1);
```

Stores prefix sum `0` once.

This handles subarrays starting from index `0`.

---

```java
int currentSum = 0;
```

Stores running prefix sum.

---

```java
int count = 0;
```

Stores number of valid subarrays found.

---

```java
currentSum += nums[i];
```

Updates prefix sum till current index.

---

```java
int need = currentSum - k;
```

Finds the prefix sum needed to make subarray sum equal to `k`.

---

```java
count += map.getOrDefault(need, 0);
```

If `need` appeared before, all those previous prefixes create valid subarrays.

---

```java
map.put(currentSum, map.getOrDefault(currentSum, 0) + 1);
```

Stores current prefix sum in the map.

---

```java
return count;
```

Returns total number of subarrays with sum `k`.

---

## Dry Run 1: Count Subarrays With Sum K

```txt
nums = [1, 2, 3]
k = 3
```

Initial:

```txt
map = {0=1}
currentSum = 0
count = 0
```

| i | nums[i] | currentSum | need = currentSum - k | map has need? | count | map after update |
|---:|---:|---:|---:|---|---:|---|
| 0 | 1 | 1 | -2 | No | 0 | {0=1, 1=1} |
| 1 | 2 | 3 | 0 | Yes, 1 time | 1 | {0=1, 1=1, 3=1} |
| 2 | 3 | 6 | 3 | Yes, 1 time | 2 | {0=1, 1=1, 3=1, 6=1} |

Answer:

```txt
2
```

Valid subarrays:

```txt
[1, 2]
[3]
```

---

## Dry Run 2: With Negative Numbers

```txt
nums = [1, -1, 1]
k = 1
```

Valid subarrays:

```txt
[1] at index 0
[1, -1, 1]
[1] at index 2
```

Answer:

```txt
3
```

Initial:

```txt
map = {0=1}
currentSum = 0
count = 0
```

| i | nums[i] | currentSum | need | map has need? | count | map after update |
|---:|---:|---:|---:|---|---:|---|
| 0 | 1 | 1 | 0 | Yes, 1 time | 1 | {0=1, 1=1} |
| 1 | -1 | 0 | -1 | No | 1 | {0=2, 1=1} |
| 2 | 1 | 1 | 0 | Yes, 2 times | 3 | {0=2, 1=2} |

Answer:

```txt
3
```

This shows why frequency is important.

Prefix sum `0` appeared two times.

---

## Example 1: Check If Subarray With Sum K Exists

Problem:

```txt
Return true if any subarray has sum k.
```

Code:

```java
import java.util.HashSet;

public boolean hasSubarraySumK(int[] nums, int k) {
    HashSet<Integer> set = new HashSet<>();

    set.add(0);

    int currentSum = 0;

    for (int i = 0; i < nums.length; i++) {
        currentSum += nums[i];

        int need = currentSum - k;

        if (set.contains(need)) {
            return true;
        }

        set.add(currentSum);
    }

    return false;
}
```

Here we only need existence, so HashSet is enough.

But for counting, use HashMap.

---

## Example 2: Longest Subarray With Sum K

Problem:

```txt
Find length of longest subarray whose sum equals k.
```

Input:

```txt
nums = [10, 5, 2, 7, 1, 9]
k = 15
```

Output:

```txt
4
```

Because:

```txt
[5, 2, 7, 1] has sum 15
```

For longest length, HashMap stores:

```txt
prefix sum → first index where it appeared
```

Code:

```java
import java.util.HashMap;

public int longestSubarraySumK(int[] nums, int k) {
    HashMap<Integer, Integer> map = new HashMap<>();

    map.put(0, -1);

    int currentSum = 0;
    int maxLength = 0;

    for (int i = 0; i < nums.length; i++) {
        currentSum += nums[i];

        int need = currentSum - k;

        if (map.containsKey(need)) {
            int length = i - map.get(need);

            if (length > maxLength) {
                maxLength = length;
            }
        }

        if (!map.containsKey(currentSum)) {
            map.put(currentSum, i);
        }
    }

    return maxLength;
}
```

---

## Why Store First Index Only?

For longest subarray, we want maximum length.

Length is:

```txt
current index - earliest previous index
```

So if the same prefix sum appears again, do not update it.

Keep the first occurrence.

That is why we write:

```java
if (!map.containsKey(currentSum)) {
    map.put(currentSum, i);
}
```

---

## Example 3: Subarray With Sum 0

Problem:

```txt
Check if any subarray has sum 0.
```

Important observation:

```txt
If same prefix sum appears twice,
then the elements between them have sum 0.
```

Example:

```txt
nums = [4, 2, -3, 1, 6]
```

Prefix sums:

```txt
4, 6, 3, 4, 10
```

Prefix sum `4` appears again.

So subarray between them has sum `0`.

Code:

```java
import java.util.HashSet;

public boolean hasZeroSumSubarray(int[] nums) {
    HashSet<Integer> set = new HashSet<>();

    set.add(0);

    int currentSum = 0;

    for (int i = 0; i < nums.length; i++) {
        currentSum += nums[i];

        if (set.contains(currentSum)) {
            return true;
        }

        set.add(currentSum);
    }

    return false;
}
```

---

## Example 4: Count Subarrays With Sum 0

Problem:

```txt
Count subarrays whose sum is 0.
```

This is the same as count subarrays with sum `k`, where:

```txt
k = 0
```

Code:

```java
import java.util.HashMap;

public int countZeroSumSubarrays(int[] nums) {
    HashMap<Integer, Integer> map = new HashMap<>();

    map.put(0, 1);

    int currentSum = 0;
    int count = 0;

    for (int i = 0; i < nums.length; i++) {
        currentSum += nums[i];

        count += map.getOrDefault(currentSum, 0);

        map.put(currentSum, map.getOrDefault(currentSum, 0) + 1);
    }

    return count;
}
```

Why no `currentSum - k`?

Because `k = 0`.

So:

```txt
currentSum - 0 = currentSum
```

---

## Example 5: Equal Number of 0s and 1s

Problem:

```txt
Find longest subarray with equal number of 0s and 1s.
```

Trick:

```txt
Convert 0 to -1
Keep 1 as +1
```

Then the problem becomes:

```txt
Find longest subarray with sum 0
```

Code:

```java
import java.util.HashMap;

public int findMaxLength(int[] nums) {
    HashMap<Integer, Integer> map = new HashMap<>();

    map.put(0, -1);

    int currentSum = 0;
    int maxLength = 0;

    for (int i = 0; i < nums.length; i++) {
        if (nums[i] == 0) {
            currentSum += -1;
        }
        else {
            currentSum += 1;
        }

        if (map.containsKey(currentSum)) {
            int length = i - map.get(currentSum);

            if (length > maxLength) {
                maxLength = length;
            }
        }
        else {
            map.put(currentSum, i);
        }
    }

    return maxLength;
}
```

---

## Prefix Sum + HashMap Variations

| Problem Type | HashMap Stores |
|---|---|
| Count subarrays with sum k | prefix sum → frequency |
| Longest subarray with sum k | prefix sum → first index |
| Check if subarray exists | prefix sums in HashSet |
| Count zero sum subarrays | prefix sum → frequency |
| Equal 0s and 1s | transformed prefix sum → first index |

---

## Prefix Sum vs Prefix Sum + HashMap

| Point | Prefix Sum | Prefix Sum + HashMap |
|---|---|---|
| Used for | Range sum queries | Subarray sum conditions |
| Example | sum from l to r | count subarrays with sum k |
| Query input | usually `[left, right]` | usually target sum `k` |
| Data structure | prefix array | HashMap |
| Handles negatives | Yes | Yes |
| Main formula | `prefix[r + 1] - prefix[l]` | `currentSum - k` |

---

## Time and Space Complexity

For count subarrays with sum k:

| Complexity | Value |
|---|---:|
| Time Complexity | O(n) average |
| Space Complexity | O(n) |

Why time is O(n)?

```txt
We scan the array once.
HashMap operations are O(1) average.
```

Why space is O(n)?

```txt
In worst case, all prefix sums are different.
```

---

## Common Mistakes

### 1. Forgetting `map.put(0, 1)`

Wrong:

```java
HashMap<Integer, Integer> map = new HashMap<>();
```

Correct:

```java
map.put(0, 1);
```

This is needed to count subarrays starting from index `0`.

---

### 2. Updating Map Before Counting

Wrong:

```java
map.put(currentSum, map.getOrDefault(currentSum, 0) + 1);
count += map.getOrDefault(currentSum - k, 0);
```

Correct:

```java
count += map.getOrDefault(currentSum - k, 0);
map.put(currentSum, map.getOrDefault(currentSum, 0) + 1);
```

First count previous prefix sums.

Then add current prefix sum.

---

### 3. Using HashSet When Count Is Needed

HashSet can check existence.

But it cannot count how many times a prefix sum appeared.

For counting, use:

```txt
HashMap
```

---

### 4. Overwriting Index in Longest Subarray Problem

Wrong:

```java
map.put(currentSum, i);
```

every time.

Correct:

```java
if (!map.containsKey(currentSum)) {
    map.put(currentSum, i);
}
```

Keep the earliest index for maximum length.

---

### 5. Confusing Range Sum Query With Subarray Count

If question gives many queries like:

```txt
[left, right]
```

Use:

```txt
Prefix Sum
```

If question asks:

```txt
how many subarrays have sum k
```

Use:

```txt
Prefix Sum + HashMap
```

---

## Beginner Checklist

Before applying Prefix Sum + HashMap, ask:

```txt
1. Is the problem about continuous subarrays?
2. Is the problem asking for exact sum k?
3. Do I need count, existence, or longest length?
4. Are negative numbers present?
5. What should HashMap store?
6. Do I need prefix sum frequency or first index?
7. Did I initialize map with 0?
8. Should I count before updating map?
9. Am I using currentSum - k correctly?
10. Is this a range query problem or subarray sum problem?
```

---

## Pattern Summary

| Point | Meaning |
|---|---|
| Pattern Name | Prefix Sum + HashMap |
| Pattern Number | 13 |
| Used For | Subarray sum problems |
| Main Formula | `oldPrefixSum = currentSum - k` |
| Count Version | prefix sum → frequency |
| Longest Version | prefix sum → first index |
| Existence Version | HashSet of prefix sums |
| Time | O(n) average |
| Space | O(n) |
| Works With Negative Numbers | Yes |

---

## Next Pattern

```txt
Pattern 14: Kadane's Algorithm
```
