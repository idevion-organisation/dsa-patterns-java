# 02. Array Pattern Identification

Pattern identification means understanding which technique should be used for a problem.

In DSA, the problem will not directly say:

```txt
Use HashMap
Use Sliding Window
Use Two Pointers
Use Prefix Sum
```

You have to identify the signal from the question.

---

## Master Pattern Signal Table

| Question Signal | Pattern to Think |
|---|---|
| Find sum / max / min / count | Traversal |
| Find an element | Linear Search |
| Sorted array + search | Binary Search |
| Sorted array + pair | Two Pointers |
| Remove or move elements in-place | In-place Overwrite |
| Check duplicates | HashSet |
| Count frequency | HashMap |
| Subarray of fixed size `k` | Sliding Window |
| Range sum query | Prefix Sum |
| Maximum subarray sum | Kadane’s Algorithm |
| Rotate / rearrange array | Reverse / Extra Array / Modular Index |
| Missing number | Math / XOR |
| Matrix/grid traversal | Nested Loops |

---

## Signal 1: Sum, Count, Max, Min

If the question asks:

```txt
sum
count
maximum
minimum
average
```

Think:

```txt
Traversal
```

Example:

```txt
Find maximum element in array.
```

Pattern:

```txt
Traversal
```

---

## Signal 2: Search

If the question asks:

```txt
Find target
Check if element exists
Return index of element
```

Think:

```txt
Linear Search
```

If the array is sorted, think:

```txt
Binary Search
```

---

## Signal 3: Duplicates

If the question talks about:

```txt
duplicate
already seen
repeated element
unique element
```

Think:

```txt
HashSet
```

Example:

```txt
Check if array contains duplicate.
```

Pattern:

```txt
HashSet
```

---

## Signal 4: Frequency

If the question asks:

```txt
How many times?
Most frequent?
Count occurrence?
Frequency of each element?
```

Think:

```txt
HashMap
```

Example:

```txt
Count frequency of each number.
```

Pattern:

```txt
HashMap
```

---

## Signal 5: Sorted Array + Pair

If array is sorted and question asks:

```txt
Find two numbers
Pair sum
Closest pair
Remove duplicates
```

Think:

```txt
Two Pointers
```

Example:

```txt
Find two numbers whose sum is target in sorted array.
```

Pattern:

```txt
Two Pointers
```

---

## Signal 6: Subarray

If the question talks about:

```txt
subarray
continuous part
window
fixed size k
maximum sum of k elements
```

Think:

```txt
Sliding Window
```

Example:

```txt
Find maximum sum of subarray of size k.
```

Pattern:

```txt
Sliding Window
```

---

## Signal 7: Range Sum

If the question asks:

```txt
sum from index l to r
multiple range queries
sum between two positions
```

Think:

```txt
Prefix Sum
```

Example:

```txt
Find sum from index 2 to 5 many times.
```

Pattern:

```txt
Prefix Sum
```

---

## Signal 8: Best / Maximum Subarray

If the question asks:

```txt
maximum subarray sum
best continuous sum
largest sum subarray
```

Think:

```txt
Kadane's Algorithm
```

Example:

```txt
nums = [-2,1,-3,4,-1,2,1,-5,4]
```

Pattern:

```txt
Kadane's Algorithm
```

---

## Quick Decision Flow

```txt
Is array sorted?
├── Yes → Binary Search / Two Pointers
└── No
    ├── Need duplicates? → HashSet
    ├── Need frequency? → HashMap
    ├── Need subarray? → Sliding Window / Prefix Sum / Kadane
    ├── Need simple sum/count/max/min? → Traversal
    └── Need in-place changes? → Two Pointers / In-place Overwrite
```

---

## Beginner Mistake

Do not choose a pattern just because you know it.

Choose pattern based on:

```txt
question signal + constraints + required output
```

---

## Quick Summary

```txt
Question words give pattern hints.
Pattern gives solution direction.
Direction makes coding easier.
```
