# Pattern 09: Merge Sorted Arrays

Merge Sorted Arrays is an important array pattern used when two sorted arrays need to be combined into one sorted result.

This pattern is based on the idea that:

```txt
If both arrays are already sorted,
we do not need to sort again.
```

We can merge them efficiently using two pointers.

---

## What Is Merge Sorted Arrays?

Suppose we have two sorted arrays:

```txt
a = [1, 3, 5]
b = [2, 4, 6]
```

Merged sorted output:

```txt
[1, 2, 3, 4, 5, 6]
```

The goal is to combine both arrays while keeping the final result sorted.

---

## Simple Meaning

```txt
Compare elements from both arrays
Pick the smaller one
Move that array pointer forward
Repeat until both arrays are fully merged
```

---

## Why This Pattern Is Useful?

A beginner may think:

```txt
Put both arrays together
Then sort again
```

That works, but it is not efficient.

If total elements are `m + n`, sorting again takes:

```txt
O((m + n) log(m + n))
```

But using Merge Sorted Arrays pattern takes:

```txt
O(m + n)
```

Because we scan both arrays only once.

---

## Pattern Signal

Think of Merge Sorted Arrays when the question says:

```txt
two sorted arrays
merge arrays
combine sorted arrays
sorted output
nums1 and nums2 are sorted
m valid elements and n valid elements
merge in-place
```

Most common signal:

```txt
Given two sorted arrays, merge them.
```

---

## Main Idea

Use three pointers:

| Pointer | Meaning |
|---|---|
| `i` | reads first array |
| `j` | reads second array |
| `k` | writes into result array |

Example:

```java
int i = 0;
int j = 0;
int k = 0;
```

Then compare:

```txt
a[i] and b[j]
```

Whichever is smaller goes into the result.

---

## Basic Merge Logic

```txt
If a[i] <= b[j]
    put a[i] in result
    move i

Else
    put b[j] in result
    move j
```

After one array ends, copy remaining elements from the other array.

---

## Complete Java Code: Merge Into New Array

```java
class Solution {
    public int[] mergeSortedArrays(int[] a, int[] b) {
        int m = a.length;
        int n = b.length;

        int[] result = new int[m + n];

        int i = 0;
        int j = 0;
        int k = 0;

        while (i < m && j < n) {
            if (a[i] <= b[j]) {
                result[k] = a[i];
                i++;
            }
            else {
                result[k] = b[j];
                j++;
            }

            k++;
        }

        while (i < m) {
            result[k] = a[i];
            i++;
            k++;
        }

        while (j < n) {
            result[k] = b[j];
            j++;
            k++;
        }

        return result;
    }
}
```

---

## Line-by-Line Explanation

```java
int m = a.length;
int n = b.length;
```

Stores the size of both arrays.

---

```java
int[] result = new int[m + n];
```

Creates a new array large enough to store all elements.

---

```java
int i = 0;
int j = 0;
int k = 0;
```

Initializes three pointers.

```txt
i → first array
j → second array
k → result array
```

---

```java
while (i < m && j < n)
```

Runs while both arrays still have elements.

---

```java
if (a[i] <= b[j])
```

Compares current elements of both arrays.

---

```java
result[k] = a[i];
i++;
```

If `a[i]` is smaller or equal, place it in result and move `i`.

---

```java
result[k] = b[j];
j++;
```

If `b[j]` is smaller, place it in result and move `j`.

---

```java
k++;
```

Move result pointer to next position.

---

```java
while (i < m)
```

Copies remaining elements from first array.

---

```java
while (j < n)
```

Copies remaining elements from second array.

---

## Dry Run: Merge Into New Array

```txt
a = [1, 3, 5]
b = [2, 4, 6]
```

Initial:

```txt
i = 0
j = 0
k = 0
result = [_, _, _, _, _, _]
```

| Step | a[i] | b[j] | Smaller | Result |
|---:|---:|---:|---:|---|
| 1 | 1 | 2 | 1 | [1, _, _, _, _, _] |
| 2 | 3 | 2 | 2 | [1, 2, _, _, _, _] |
| 3 | 3 | 4 | 3 | [1, 2, 3, _, _, _] |
| 4 | 5 | 4 | 4 | [1, 2, 3, 4, _, _] |
| 5 | 5 | 6 | 5 | [1, 2, 3, 4, 5, _] |

Now first array is finished.

Copy remaining from second array:

```txt
6
```

Final result:

```txt
[1, 2, 3, 4, 5, 6]
```

---

## Important Variation: Merge In-place from End

Some problems do not ask us to create a new array.

They give:

```txt
nums1 has extra empty space at the end
nums2 needs to be merged into nums1
```

Example:

```txt
nums1 = [1, 2, 3, 0, 0, 0], m = 3
nums2 = [2, 5, 6], n = 3
```

Only first `m` values in `nums1` are valid:

```txt
[1, 2, 3]
```

The zeroes are empty space.

Final output inside `nums1` should be:

```txt
[1, 2, 2, 3, 5, 6]
```

---

## Why Merge from End?

If we merge from the front, we may overwrite useful values in `nums1`.

Example:

```txt
nums1 = [1, 2, 3, 0, 0, 0]
nums2 = [2, 5, 6]
```

If we start writing from index `0`, the original `1, 2, 3` may get disturbed.

So we merge from the end.

---

## Main Variables for In-place Merge

| Pointer | Meaning |
|---|---|
| `i` | last valid element of nums1 |
| `j` | last element of nums2 |
| `k` | last position of nums1 |

Initialize:

```java
int i = m - 1;
int j = n - 1;
int k = m + n - 1;
```

---

## In-place Merge Logic

Compare from the end:

```txt
nums1[i] and nums2[j]
```

Put the larger value at `nums1[k]`.

Then move the pointer of the used value.

---

## Complete Java Code: Merge In-place

```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int i = m - 1;
        int j = n - 1;
        int k = m + n - 1;

        while (i >= 0 && j >= 0) {
            if (nums1[i] > nums2[j]) {
                nums1[k] = nums1[i];
                i--;
            }
            else {
                nums1[k] = nums2[j];
                j--;
            }

            k--;
        }

        while (j >= 0) {
            nums1[k] = nums2[j];
            j--;
            k--;
        }
    }
}
```

---

## Why Only Copy Remaining `nums2`?

After the main loop, two cases are possible.

Case 1:

```txt
nums2 still has elements
```

Then we must copy them into `nums1`.

Case 2:

```txt
nums1 still has elements
```

Then they are already in the correct place.

So we only need:

```java
while (j >= 0)
```

---

## Dry Run: In-place Merge

```txt
nums1 = [1, 2, 3, 0, 0, 0], m = 3
nums2 = [2, 5, 6], n = 3
```

Initial:

```txt
i = 2 → nums1[i] = 3
j = 2 → nums2[j] = 6
k = 5
```

| Step | nums1[i] | nums2[j] | Bigger | Place at k | nums1 |
|---:|---:|---:|---:|---:|---|
| 1 | 3 | 6 | 6 | 5 | [1, 2, 3, 0, 0, 6] |
| 2 | 3 | 5 | 5 | 4 | [1, 2, 3, 0, 5, 6] |
| 3 | 3 | 2 | 3 | 3 | [1, 2, 3, 3, 5, 6] |
| 4 | 2 | 2 | 2 | 2 | [1, 2, 2, 3, 5, 6] |

Now:

```txt
j = -1
```

nums2 is finished.

Final:

```txt
[1, 2, 2, 3, 5, 6]
```

---

## Merge Sorted Arrays vs Sorting

| Point | Sorting Again | Merge Pattern |
|---|---|---|
| Uses sorted input? | No | Yes |
| Time | O((m+n) log(m+n)) | O(m+n) |
| Approach | Combine then sort | Compare and place |
| Better for sorted arrays | No | Yes |

If arrays are already sorted, merging is better.

---

## Merge Sorted Arrays vs Two Pointers

Merge Sorted Arrays is a special use of Two Pointers.

| Point | Two Pointers | Merge Sorted Arrays |
|---|---|---|
| Pointer use | Compare/move two positions | Compare elements from two arrays |
| Common goal | Pair/reverse/check | Build sorted result |
| Movement | Depends on condition | Smaller/larger element moves |
| Output | Often value/check | New or modified sorted array |

---

## Example 1: Merge With Duplicates

Input:

```txt
a = [1, 2, 2]
b = [2, 3]
```

Output:

```txt
[1, 2, 2, 2, 3]
```

Important:

```txt
Normal merge keeps duplicates.
```

---

## Example 2: Merge Unique Elements

Input:

```txt
a = [1, 2, 2]
b = [2, 3]
```

Output:

```txt
[1, 2, 3]
```

In this case, we need an extra condition to avoid adding duplicate values.

This is a variation of merge sorted arrays.

---

## Example 3: Intersection of Two Sorted Arrays

Input:

```txt
a = [1, 2, 2, 3]
b = [2, 2, 4]
```

Output:

```txt
[2, 2]
```

Idea:

```txt
If a[i] == b[j], add it and move both pointers.
If a[i] < b[j], move i.
If a[i] > b[j], move j.
```

This also uses the sorted merge idea.

---

## Time and Space Complexity

For merge into new array:

| Complexity | Value |
|---|---:|
| Time Complexity | O(m + n) |
| Space Complexity | O(m + n) |

Because we create a new result array.

---

For in-place merge:

| Complexity | Value |
|---|---:|
| Time Complexity | O(m + n) |
| Space Complexity | O(1) |

Because we modify `nums1` directly.

---

## Common Mistakes

### 1. Sorting Again Instead of Merging

Wrong approach for already sorted arrays:

```java
Arrays.sort(result);
```

Better:

```txt
Use two pointers and merge in O(m+n).
```

---

### 2. Merging In-place from Front

Wrong for LeetCode-style merge:

```txt
Start writing from index 0
```

This can overwrite valid elements in `nums1`.

Correct:

```txt
Merge from the end.
```

---

### 3. Confusing `m` and `nums1.length`

In in-place merge:

```txt
m = number of valid elements in nums1
nums1.length = total capacity
```

Example:

```txt
nums1 = [1, 2, 3, 0, 0, 0]
m = 3
nums1.length = 6
```

Do not treat all 6 values as valid.

---

### 4. Forgetting Remaining Elements

After main merge loop, one array may still have elements.

For new array merge, copy both remaining parts:

```java
while (i < m)
while (j < n)
```

For in-place merge, copy remaining `nums2`:

```java
while (j >= 0)
```

---

### 5. Using Wrong Pointer Direction

For new result array:

```txt
start from front
```

For in-place `nums1` merge:

```txt
start from end
```

---

## Beginner Checklist

Before applying Merge Sorted Arrays, ask:

```txt
1. Are both arrays sorted?
2. Do I need a new result array?
3. Do I need to merge in-place?
4. If in-place, does nums1 have extra space?
5. Should I start from front or end?
6. Are duplicates allowed?
7. Should I preserve all values or only unique values?
8. What should happen when one array finishes?
9. What is the time complexity?
```

---

## Pattern Summary

| Point | Meaning |
|---|---|
| Pattern Name | Merge Sorted Arrays |
| Pattern Number | 09 |
| Used For | Combining sorted arrays |
| Main Variables | `i`, `j`, `k` |
| New Array Merge | Start from front |
| In-place Merge | Start from end |
| Time | O(m + n) |
| Space | O(m + n) or O(1) |
| Key Benefit | Avoids sorting again |

---

## Next Pattern

```txt
Pattern 10: Fixed Size Sliding Window
```
