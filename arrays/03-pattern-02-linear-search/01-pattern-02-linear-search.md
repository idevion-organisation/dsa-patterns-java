# Pattern 02: Linear Search

Linear Search is a searching pattern used to find an element by checking array elements one by one.

It is one of the simplest and most important patterns in arrays.

---

## What Is Linear Search?

Linear Search means checking every element from start to end until we find the target.

Example:

```txt
nums = [4, 7, 1, 9, 3]
target = 9
```

We check:

```txt
4 → not target
7 → not target
1 → not target
9 → target found
```

Answer:

```txt
index = 3
```

Because `9` is present at index `3`.

---

## Simple Meaning

```txt
Start from index 0
Check each element
If target is found, return answer
If target is not found after full array, return not found
```

---

## When to Use Linear Search?

Use Linear Search when:

```txt
array is unsorted
need to find a target
need to check if element exists
need to return index of an element
need to count occurrences
need to find first or last occurrence
```

The most common signal is:

```txt
Find target in array
```

---

## Pattern Signal

If the question says:

```txt
find element
search target
check if target exists
return index
find first occurrence
find last occurrence
count occurrence
```

Think:

```txt
Linear Search
```

---

## Linear Search vs Traversal

Traversal and Linear Search are related, but not exactly the same.

| Point | Traversal | Linear Search |
|---|---|---|
| Meaning | Visit every element | Search for a target |
| Stops early? | Usually no | Yes, if target is found |
| Used for | Sum, max, min, count | Find target/index/existence |
| Example | Sum of array | Find index of target |

Traversal checks all elements.

Linear Search can stop early when the target is found.

---

## Basic Logic

For every index `i`:

```txt
if nums[i] == target
    return i
```

If loop ends and target is not found:

```txt
return -1
```

---

## Complete Java Code

```java
class Solution {
    public int linearSearch(int[] nums, int target) {
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] == target) {
                return i;
            }
        }

        return -1;
    }
}
```

---

## Line-by-Line Explanation

```java
public int linearSearch(int[] nums, int target)
```

This method takes:

```txt
nums   → input array
target → element we want to find
```

It returns:

```txt
index of target if found
-1 if target is not found
```

---

```java
for (int i = 0; i < nums.length; i++)
```

This loop starts from index `0` and goes till the last index.

---

```java
if (nums[i] == target)
```

This checks whether the current element is equal to the target.

---

```java
return i;
```

If target is found, return its index immediately.

This is called **early return**.

---

```java
return -1;
```

If the loop finishes and target is not found, return `-1`.

---

## Why Do We Return `-1`?

Array indexes start from `0`.

Valid indexes are:

```txt
0, 1, 2, 3, ...
```

So `-1` is not a valid index.

That is why we use `-1` to represent:

```txt
target not found
```

---

## Dry Run 1: Target Found

```txt
nums = [4, 7, 1, 9, 3]
target = 9
```

| Step | `i` | `nums[i]` | Check | Result |
|---:|---:|---:|---|---|
| 1 | 0 | 4 | 4 == 9 | false |
| 2 | 1 | 7 | 7 == 9 | false |
| 3 | 2 | 1 | 1 == 9 | false |
| 4 | 3 | 9 | 9 == 9 | true |

Target found at:

```txt
index = 3
```

Return:

```txt
3
```

---

## Dry Run 2: Target Not Found

```txt
nums = [4, 7, 1, 9, 3]
target = 6
```

| Step | `i` | `nums[i]` | Check | Result |
|---:|---:|---:|---|---|
| 1 | 0 | 4 | 4 == 6 | false |
| 2 | 1 | 7 | 7 == 6 | false |
| 3 | 2 | 1 | 1 == 6 | false |
| 4 | 3 | 9 | 9 == 6 | false |
| 5 | 4 | 3 | 3 == 6 | false |

Loop ends.

Target not found.

Return:

```txt
-1
```

---

## Example 1: Return Index

Problem:

```txt
Find the index of target in array.
```

Input:

```txt
nums = [10, 20, 30, 40]
target = 30
```

Code:

```java
public int search(int[] nums, int target) {
    for (int i = 0; i < nums.length; i++) {
        if (nums[i] == target) {
            return i;
        }
    }

    return -1;
}
```

Output:

```txt
2
```

---

## Example 2: Return True or False

Problem:

```txt
Check if target exists in array.
```

Input:

```txt
nums = [5, 8, 2, 6]
target = 8
```

Code:

```java
public boolean containsTarget(int[] nums, int target) {
    for (int i = 0; i < nums.length; i++) {
        if (nums[i] == target) {
            return true;
        }
    }

    return false;
}
```

Output:

```txt
true
```

---

## Example 3: Count Occurrences

Problem:

```txt
Count how many times target appears.
```

Input:

```txt
nums = [2, 3, 2, 4, 2]
target = 2
```

Code:

```java
public int countTarget(int[] nums, int target) {
    int count = 0;

    for (int i = 0; i < nums.length; i++) {
        if (nums[i] == target) {
            count++;
        }
    }

    return count;
}
```

Output:

```txt
3
```

Important:

```txt
For count, do not return early.
You must check the full array.
```

---

## Example 4: First Occurrence

Problem:

```txt
Find first index of target.
```

Input:

```txt
nums = [5, 2, 7, 2, 9]
target = 2
```

Code:

```java
public int firstOccurrence(int[] nums, int target) {
    for (int i = 0; i < nums.length; i++) {
        if (nums[i] == target) {
            return i;
        }
    }

    return -1;
}
```

Output:

```txt
1
```

This returns the first `2`.

---

## Example 5: Last Occurrence

Problem:

```txt
Find last index of target.
```

Input:

```txt
nums = [5, 2, 7, 2, 9]
target = 2
```

Code:

```java
public int lastOccurrence(int[] nums, int target) {
    int ans = -1;

    for (int i = 0; i < nums.length; i++) {
        if (nums[i] == target) {
            ans = i;
        }
    }

    return ans;
}
```

Output:

```txt
3
```

Why not return immediately?

```txt
Because we need the last occurrence.
```

So we keep updating `ans`.

---

## Example 6: Linear Search in 2D Array

Problem:

```txt
Find target in matrix.
```

Input:

```txt
matrix = [
  [1, 2, 3],
  [4, 5, 6]
]

target = 5
```

Code:

```java
public boolean searchMatrix(int[][] matrix, int target) {
    for (int i = 0; i < matrix.length; i++) {
        for (int j = 0; j < matrix[0].length; j++) {
            if (matrix[i][j] == target) {
                return true;
            }
        }
    }

    return false;
}
```

Output:

```txt
true
```

Time:

```txt
O(rows × columns)
```

---

## Time and Space Complexity

For 1D array:

| Case | Time |
|---|---:|
| Best Case | O(1) |
| Worst Case | O(n) |
| Average Case | O(n) |

Best case:

```txt
Target is at first index.
```

Worst case:

```txt
Target is at last index or not present.
```

Space complexity:

```txt
O(1)
```

Because we use only a few variables.

---

## Linear Search vs Binary Search

| Point | Linear Search | Binary Search |
|---|---|---|
| Works on unsorted array | Yes | No |
| Requires sorted array | No | Yes |
| Checks | One by one | Middle element |
| Time | O(n) | O(log n) |
| Beginner use | Basic searching | Optimized searching |

Important:

```txt
If array is unsorted, Linear Search is the safest search method.
If array is sorted, Binary Search may be better.
```

---

## Common Mistakes

### 1. Returning Too Early

Wrong for counting:

```java
for (int i = 0; i < nums.length; i++) {
    if (nums[i] == target) {
        return 1;
    }
}
```

This only checks if target exists.

Correct for count:

```java
int count = 0;

for (int i = 0; i < nums.length; i++) {
    if (nums[i] == target) {
        count++;
    }
}

return count;
```

---

### 2. Using `<= nums.length`

Wrong:

```java
for (int i = 0; i <= nums.length; i++)
```

Correct:

```java
for (int i = 0; i < nums.length; i++)
```

---

### 3. Returning Value Instead of Index

If question asks for index:

Wrong:

```java
return nums[i];
```

Correct:

```java
return i;
```

---

### 4. Forgetting Not Found Case

Wrong:

```java
public int search(int[] nums, int target) {
    for (int i = 0; i < nums.length; i++) {
        if (nums[i] == target) {
            return i;
        }
    }
}
```

Correct:

```java
return -1;
```

after the loop.

---

### 5. Using Binary Search on Unsorted Array

If array is unsorted:

```txt
[7, 2, 9, 1]
```

Do not directly use Binary Search.

Use:

```txt
Linear Search
```

---

## Beginner Checklist

Before solving a Linear Search problem, ask:

```txt
1. What is the target?
2. Is the array sorted or unsorted?
3. Do I need index, true/false, count, or value?
4. Should I stop after finding the target?
5. Do I need first occurrence or last occurrence?
6. What should I return if target is not found?
7. Am I using i < nums.length?
8. Am I returning index or value correctly?
```

---

## Pattern Summary

| Point | Meaning |
|---|---|
| Pattern Name | Linear Search |
| Pattern Number | 02 |
| Used For | Finding target in array |
| Works On | Sorted and unsorted arrays |
| Main Logic | Check elements one by one |
| Best Time | O(1) |
| Worst Time | O(n) |
| Space | O(1) |
| Not Found Return | Usually `-1` or `false` |

---

## Next Pattern

```txt
Pattern 03: Binary Search
```
