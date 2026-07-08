# Pattern 03: Binary Search

Binary Search is a searching pattern used to find an element faster by repeatedly dividing the search space into half.

It is one of the most important array patterns.

---

## What Is Binary Search?

Suppose we have a sorted array:

```txt
nums = [2, 4, 6, 8, 10, 12]
target = 10
```

Linear Search checks one by one:

```txt
2 → 4 → 6 → 8 → 10
```

Binary Search checks the middle element first.

```txt
middle = 6
```

Since `10` is greater than `6`, we ignore the left half.

Now we only search:

```txt
[8, 10, 12]
```

Again, check the middle.

```txt
middle = 10
```

Target found.

---

## Simple Meaning

```txt
Find middle
Compare target with middle
Remove half of the search space
Repeat until target is found or search space ends
```

---

## Most Important Condition

Binary Search usually works when the array is sorted.

Sorted array:

```txt
[1, 3, 5, 7, 9]
```

Unsorted array:

```txt
[7, 1, 9, 3, 5]
```

Do not directly apply Binary Search on an unsorted array.

Beginner rule:

```txt
Sorted array + search target = Binary Search
```

---

## When to Use Binary Search?

Use Binary Search when the question says:

```txt
sorted array
search target
find index
find position
insert position
first occurrence
last occurrence
minimum possible answer
maximum possible answer
```

For beginner array problems, start with:

```txt
Search in sorted array
```

---

## Pattern Signal

If the question contains words like:

```txt
sorted
search
target
position
first index
last index
insert
minimum possible
maximum possible
```

Think:

```txt
Binary Search
```

---

## Why Binary Search Is Fast?

If array size is:

```txt
n = 16
```

Binary Search reduces it like:

```txt
16 → 8 → 4 → 2 → 1
```

Every step removes half of the search space.

So the time complexity is:

```txt
O(log n)
```

---

## Main Variables

Binary Search mainly uses three variables:

| Variable | Meaning |
|---|---|
| `left` | starting index of current search space |
| `right` | ending index of current search space |
| `mid` | middle index of current search space |

Initial values:

```java
int left = 0;
int right = nums.length - 1;
```

Middle index:

```java
int mid = left + (right - left) / 2;
```

---

## Why Use This Mid Formula?

You may see this:

```java
int mid = (left + right) / 2;
```

But better formula is:

```java
int mid = left + (right - left) / 2;
```

Reason:

```txt
It avoids integer overflow when left and right are very large.
```

So always prefer:

```java
int mid = left + (right - left) / 2;
```

---

## Core Logic

After finding `mid`, compare:

```txt
nums[mid] and target
```

There are three cases:

```txt
nums[mid] == target → answer found
nums[mid] < target  → search right side
nums[mid] > target  → search left side
```

In Java:

```java
if (nums[mid] == target) {
    return mid;
}
else if (nums[mid] < target) {
    left = mid + 1;
}
else {
    right = mid - 1;
}
```

---

## Complete Java Code

```java
class Solution {
    public int search(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (nums[mid] == target) {
                return mid;
            }
            else if (nums[mid] < target) {
                left = mid + 1;
            }
            else {
                right = mid - 1;
            }
        }

        return -1;
    }
}
```

---

## Line-by-Line Explanation

```java
int left = 0;
```

Search starts from the first index.

```java
int right = nums.length - 1;
```

Search ends at the last index.

```java
while (left <= right)
```

Loop runs while the search space is valid.

```java
int mid = left + (right - left) / 2;
```

Find the middle index.

```java
if (nums[mid] == target)
```

If middle element is equal to target, return `mid`.

```java
else if (nums[mid] < target)
```

If middle element is smaller than target, target must be on the right side.

```java
left = mid + 1;
```

Remove the left half including `mid`.

```java
else
```

If middle element is greater than target, target must be on the left side.

```java
right = mid - 1;
```

Remove the right half including `mid`.

```java
return -1;
```

If target is not found, return `-1`.

---

## Why `left <= right`?

Search space is valid while:

```txt
left <= right
```

Example:

```txt
left = 2
right = 2
```

There is still one element left to check.

So we must allow the loop to run.

That is why we use:

```java
while (left <= right)
```

---

## Dry Run 1: Target Found

```txt
nums = [2, 4, 6, 8, 10, 12]
target = 10
```

Initial values:

```txt
left = 0
right = 5
```

| Step | left | right | mid | nums[mid] | Decision |
|---:|---:|---:|---:|---:|---|
| 1 | 0 | 5 | 2 | 6 | 6 < 10, search right |
| 2 | 3 | 5 | 4 | 10 | target found |

Answer:

```txt
4
```

Because `10` is present at index `4`.

---

## Dry Run 2: Target Not Found

```txt
nums = [2, 4, 6, 8, 10, 12]
target = 7
```

| Step | left | right | mid | nums[mid] | Decision |
|---:|---:|---:|---:|---:|---|
| 1 | 0 | 5 | 2 | 6 | 6 < 7, search right |
| 2 | 3 | 5 | 4 | 10 | 10 > 7, search left |
| 3 | 3 | 3 | 3 | 8 | 8 > 7, search left |

Now:

```txt
left = 3
right = 2
```

Condition:

```txt
left <= right
3 <= 2 → false
```

Answer:

```txt
-1
```

---

## Example 1: Search Target Index

Problem:

```txt
Return index of target in sorted array.
```

Input:

```txt
nums = [1, 3, 5, 7, 9]
target = 7
```

Output:

```txt
3
```

Code:

```java
public int search(int[] nums, int target) {
    int left = 0;
    int right = nums.length - 1;

    while (left <= right) {
        int mid = left + (right - left) / 2;

        if (nums[mid] == target) {
            return mid;
        }
        else if (nums[mid] < target) {
            left = mid + 1;
        }
        else {
            right = mid - 1;
        }
    }

    return -1;
}
```

---

## Example 2: Return True or False

Problem:

```txt
Check if target exists in sorted array.
```

Input:

```txt
nums = [10, 20, 30, 40]
target = 30
```

Output:

```txt
true
```

Code:

```java
public boolean containsTarget(int[] nums, int target) {
    int left = 0;
    int right = nums.length - 1;

    while (left <= right) {
        int mid = left + (right - left) / 2;

        if (nums[mid] == target) {
            return true;
        }
        else if (nums[mid] < target) {
            left = mid + 1;
        }
        else {
            right = mid - 1;
        }
    }

    return false;
}
```

---

## Example 3: Search Insert Position

Problem:

```txt
Return index if target exists.
Otherwise return the position where target should be inserted.
```

Input:

```txt
nums = [1, 3, 5, 6]
target = 2
```

Output:

```txt
1
```

Why?

```txt
2 should be inserted at index 1.
```

Code:

```java
public int searchInsert(int[] nums, int target) {
    int left = 0;
    int right = nums.length - 1;

    while (left <= right) {
        int mid = left + (right - left) / 2;

        if (nums[mid] == target) {
            return mid;
        }
        else if (nums[mid] < target) {
            left = mid + 1;
        }
        else {
            right = mid - 1;
        }
    }

    return left;
}
```

Why return `left`?

```txt
When loop ends, left points to the correct insertion position.
```

---

## Example 4: First Occurrence

Problem:

```txt
Find first index of target in sorted array with duplicates.
```

Input:

```txt
nums = [1, 2, 2, 2, 3]
target = 2
```

Output:

```txt
1
```

Code:

```java
public int firstOccurrence(int[] nums, int target) {
    int left = 0;
    int right = nums.length - 1;
    int ans = -1;

    while (left <= right) {
        int mid = left + (right - left) / 2;

        if (nums[mid] == target) {
            ans = mid;
            right = mid - 1;
        }
        else if (nums[mid] < target) {
            left = mid + 1;
        }
        else {
            right = mid - 1;
        }
    }

    return ans;
}
```

Why move left side after finding target?

```txt
Because target may also exist before mid.
```

---

## Example 5: Last Occurrence

Problem:

```txt
Find last index of target in sorted array with duplicates.
```

Input:

```txt
nums = [1, 2, 2, 2, 3]
target = 2
```

Output:

```txt
3
```

Code:

```java
public int lastOccurrence(int[] nums, int target) {
    int left = 0;
    int right = nums.length - 1;
    int ans = -1;

    while (left <= right) {
        int mid = left + (right - left) / 2;

        if (nums[mid] == target) {
            ans = mid;
            left = mid + 1;
        }
        else if (nums[mid] < target) {
            left = mid + 1;
        }
        else {
            right = mid - 1;
        }
    }

    return ans;
}
```

Why move right side after finding target?

```txt
Because target may also exist after mid.
```

---

## Time and Space Complexity

| Complexity | Value |
|---|---:|
| Time Complexity | O(log n) |
| Space Complexity | O(1) |

Why time is `O(log n)`?

```txt
Because every step removes half of the search space.
```

Why space is `O(1)`?

```txt
Because only left, right, mid, and few variables are used.
```

---

## Linear Search vs Binary Search

| Point | Linear Search | Binary Search |
|---|---|---|
| Works on unsorted array | Yes | No |
| Requires sorted array | No | Yes |
| Search method | One by one | Middle element |
| Time complexity | O(n) | O(log n) |
| Best use | Unsorted/small arrays | Sorted arrays |

---

## Common Mistakes

### 1. Applying Binary Search on Unsorted Array

Wrong:

```txt
nums = [8, 2, 10, 4]
```

Correct:

```txt
Use Binary Search only when array is sorted.
```

---

### 2. Infinite Loop Mistake

Wrong:

```java
left = mid;
right = mid;
```

Correct:

```java
left = mid + 1;
right = mid - 1;
```

---

### 3. Returning Value Instead of Index

If question asks for index:

Wrong:

```java
return nums[mid];
```

Correct:

```java
return mid;
```

---

### 4. Forgetting Not Found Case

Always return after loop:

```java
return -1;
```

---

### 5. Wrong Side Movement

If:

```java
nums[mid] < target
```

Then target is on right side:

```java
left = mid + 1;
```

If:

```java
nums[mid] > target
```

Then target is on left side:

```java
right = mid - 1;
```

---

## Beginner Checklist

Before using Binary Search, ask:

```txt
1. Is the array sorted?
2. What is the target?
3. Do I need index, true/false, or position?
4. What should I return if target is not found?
5. Am I using left <= right?
6. Am I calculating mid correctly?
7. Am I moving left and right correctly?
8. Am I avoiding infinite loop?
```

---

## Pattern Summary

| Point | Meaning |
|---|---|
| Pattern Name | Binary Search |
| Pattern Number | 03 |
| Used For | Searching efficiently |
| Main Condition | Array should be sorted |
| Main Variables | `left`, `right`, `mid` |
| Best Time | O(1) |
| Worst Time | O(log n) |
| Space | O(1) |
| Not Found Return | Usually `-1` or `false` |

---

## Next Pattern

```txt
Pattern 04: Two Pointers
```
