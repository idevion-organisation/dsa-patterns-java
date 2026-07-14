# Day 11 Practice: Pattern 09 Merge Sorted Arrays

Today's goal is to master the **Merge Sorted Arrays Pattern**.

This pattern is used when two sorted arrays need to be combined, compared, or processed together.

---

## Practice Method

For every problem, write:

```txt
Given:
Asked:
Are both arrays sorted?
Need new array or in-place?
Should duplicates be kept?
Pointer meaning:
Pattern:
Return:
Time Complexity:
Space Complexity:
```

Example:

```txt
Problem: Merge two sorted arrays

Given: two sorted integer arrays
Asked: return one sorted merged array
Are both arrays sorted? yes
Need new array or in-place? new array
Should duplicates be kept? yes
Pointer meaning: i for first array, j for second array, k for result
Pattern: Merge Sorted Arrays
Return: merged array
Time: O(m + n)
Space: O(m + n)
```

---

## Manual Practice Problems

### 1. Merge Two Sorted Arrays

```txt
Input:
a = [1, 3, 5]
b = [2, 4, 6]

Output:
[1, 2, 3, 4, 5, 6]
```

Think:

```txt
Compare a[i] and b[j].
Pick smaller value.
```

---

### 2. Merge With Duplicates

```txt
Input:
a = [1, 2, 2]
b = [2, 3]

Output:
[1, 2, 2, 2, 3]
```

Think:

```txt
Normal merge keeps duplicates.
```

---

### 3. Merge When First Array Ends Early

```txt
Input:
a = [1, 2]
b = [3, 4, 5]

Output:
[1, 2, 3, 4, 5]
```

Think:

```txt
After a ends, copy remaining elements from b.
```

---

### 4. Merge When Second Array Ends Early

```txt
Input:
a = [1, 4, 5]
b = [2]

Output:
[1, 2, 4, 5]
```

Think:

```txt
After b ends, copy remaining elements from a.
```

---

### 5. Merge nums2 Into nums1 In-place

```txt
Input:
nums1 = [1, 2, 3, 0, 0, 0], m = 3
nums2 = [2, 5, 6], n = 3

Output:
[1, 2, 2, 3, 5, 6]
```

Think:

```txt
Start from the end.
Place larger value at nums1[k].
```

---

### 6. Intersection With Duplicates

```txt
Input:
a = [1, 2, 2, 3]
b = [2, 2, 4]

Output:
[2, 2]
```

Think:

```txt
If values are equal, add value and move both pointers.
```

---

### 7. Intersection Unique

```txt
Input:
a = [1, 2, 2, 3]
b = [2, 2, 4]

Output:
[2]
```

Think:

```txt
Add common value only once.
Skip repeated duplicates.
```

---

### 8. Union of Two Sorted Arrays

```txt
Input:
a = [1, 2, 2, 3]
b = [2, 3, 4]

Output:
[1, 2, 3, 4]
```

Think:

```txt
Merge both arrays but avoid duplicates.
```

---

### 9. Median After Merging

```txt
Input:
a = [1, 3]
b = [2]

Output:
2.0
```

Merged:

```txt
[1, 2, 3]
```

Median:

```txt
2
```

---

## Dry Run Practice

Dry run this manually:

```txt
a = [1, 3, 5]
b = [2, 4, 6]
```

Fill this table:

| Step | i | j | a[i] | b[j] | Pick | Result |
|---:|---:|---:|---:|---:|---:|---|
| 1 |  |  |  |  |  |  |
| 2 |  |  |  |  |  |  |
| 3 |  |  |  |  |  |  |
| 4 |  |  |  |  |  |  |
| 5 |  |  |  |  |  |  |

---

## Completed Dry Run Answer

```txt
a = [1, 3, 5]
b = [2, 4, 6]
```

| Step | i | j | a[i] | b[j] | Pick | Result |
|---:|---:|---:|---:|---:|---:|---|
| 1 | 0 | 0 | 1 | 2 | 1 | [1] |
| 2 | 1 | 0 | 3 | 2 | 2 | [1, 2] |
| 3 | 1 | 1 | 3 | 4 | 3 | [1, 2, 3] |
| 4 | 2 | 1 | 5 | 4 | 4 | [1, 2, 3, 4] |
| 5 | 2 | 2 | 5 | 6 | 5 | [1, 2, 3, 4, 5] |

Copy remaining:

```txt
6
```

Final:

```txt
[1, 2, 3, 4, 5, 6]
```

---

## In-place Merge Dry Run Practice

Dry run:

```txt
nums1 = [1, 2, 3, 0, 0, 0], m = 3
nums2 = [2, 5, 6], n = 3
```

Fill this table:

| Step | i | j | k | nums1[i] | nums2[j] | Place | nums1 |
|---:|---:|---:|---:|---:|---:|---:|---|
| 1 |  |  |  |  |  |  |  |
| 2 |  |  |  |  |  |  |  |
| 3 |  |  |  |  |  |  |  |
| 4 |  |  |  |  |  |  |  |

---

## Completed In-place Dry Run Answer

```txt
nums1 = [1, 2, 3, 0, 0, 0], m = 3
nums2 = [2, 5, 6], n = 3
```

| Step | i | j | k | nums1[i] | nums2[j] | Place | nums1 |
|---:|---:|---:|---:|---:|---:|---:|---|
| 1 | 2 | 2 | 5 | 3 | 6 | 6 | [1, 2, 3, 0, 0, 6] |
| 2 | 2 | 1 | 4 | 3 | 5 | 5 | [1, 2, 3, 0, 5, 6] |
| 3 | 2 | 0 | 3 | 3 | 2 | 3 | [1, 2, 3, 3, 5, 6] |
| 4 | 1 | 0 | 2 | 2 | 2 | 2 | [1, 2, 2, 3, 5, 6] |

Final:

```txt
[1, 2, 2, 3, 5, 6]
```

---

## Common Mistake Practice

### Mistake 1

Find the issue:

```java
Arrays.sort(result);
```

after combining two sorted arrays.

Problem:

```txt
This ignores the advantage of already sorted arrays.
```

Better:

```txt
Use merge pattern in O(m+n).
```

---

### Mistake 2

Find the issue:

```txt
Merging nums2 into nums1 from index 0.
```

Problem:

```txt
It can overwrite valid elements in nums1.
```

Correct:

```txt
Merge from the end using i, j, and k.
```

---

### Mistake 3

Find the error:

```java
int i = nums1.length - 1;
```

for in-place merge.

Problem:

```txt
nums1.length includes empty zero spaces.
```

Correct:

```java
int i = m - 1;
```

---

### Mistake 4

Find the issue:

```txt
After main loop, nums2 still has elements.
```

Mistake:

```txt
Not copying remaining nums2 values.
```

Correct:

```java
while (j >= 0) {
    nums1[k] = nums2[j];
    j--;
    k--;
}
```

---

### Mistake 5

Find the issue:

```txt
Question asks for unique merged array.
```

Mistake:

```txt
Normal merge adds all duplicates.
```

Correct:

```txt
Add duplicate-check condition before adding to result.
```

---

## LeetCode Practice

| No. | Problem | Concept |
|---:|---|---|
| 88 | Merge Sorted Array | In-place merge from end |
| 21 | Merge Two Sorted Lists | Same merge logic on linked list |
| 350 | Intersection of Two Arrays II | Common elements with duplicate count |
| 349 | Intersection of Two Arrays | Unique intersection |
| 4 | Median of Two Sorted Arrays | Merge + median beginner approach |
| 977 | Squares of a Sorted Array | Two-side merge-style filling |
| 2570 | Merge Two 2D Arrays by Summing Values | Merge sorted IDs |
| 986 | Interval List Intersections | Two sorted lists comparison |

---

## Answer Key

| Problem | Pattern | Time | Space |
|---:|---|---:|---:|
| 1 | Merge Sorted Arrays | O(m+n) | O(m+n) |
| 2 | Merge Sorted Arrays | O(m+n) | O(m+n) |
| 3 | Merge Sorted Arrays | O(m+n) | O(m+n) |
| 4 | Merge Sorted Arrays | O(m+n) | O(m+n) |
| 5 | In-place Merge | O(m+n) | O(1) |
| 6 | Sorted Intersection | O(m+n) | O(min(m,n)) |
| 7 | Unique Sorted Intersection | O(m+n) | O(min(m,n)) |
| 8 | Sorted Union | O(m+n) | O(m+n) |
| 9 | Merge + Median | O(m+n) | O(m+n) |

---

## Before Moving to Pattern 10

You should be able to:

| Skill | Status |
|---|---|
| Explain Merge Sorted Arrays | ✅ |
| Use `i`, `j`, and `k` pointers | ✅ |
| Merge two sorted arrays into a new array | ✅ |
| Copy remaining elements | ✅ |
| Merge nums2 into nums1 in-place | ✅ |
| Explain why in-place merge starts from end | ✅ |
| Handle duplicates correctly | ✅ |
| Find intersection of sorted arrays | ✅ |
| Find union of sorted arrays | ✅ |
| Explain O(m+n) time | ✅ |
| Avoid sorting again unnecessarily | ✅ |

---

## Next Topic

```txt
Pattern 10: Fixed Size Sliding Window
```
