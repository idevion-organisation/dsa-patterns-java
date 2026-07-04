# 02. Array Complexity

Time complexity tells how fast or slow an operation becomes when input size increases.

---

## Array Operation Table

| Operation | Time | Reason |
|---|---:|---|
| Access by index | O(1) | Direct access |
| Update by index | O(1) | Direct update |
| Traverse full array | O(n) | Visit all elements |
| Search in unsorted array | O(n) | May check all elements |
| Search in sorted array | O(log n) | Binary search |
| Insert/delete in middle | O(n) | Java arrays are fixed-size; shifting/new array may be needed |
| Sort array | O(n log n) | Sorting cost |

---

## Important Ideas

### O(1): Direct Access

```java
arr[2]
```

Direct index access takes constant time.

---

### O(n): One Loop

```java
for (int i = 0; i < arr.length; i++) {
    System.out.println(arr[i]);
}
```

If array has `n` elements, loop runs `n` times.

---

### O(n²): Nested Loops

```java
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        // work
    }
}
```

Nested loops usually mean O(n²).

---

### O(log n): Divide Search Space

Binary search works when the array is sorted.

```txt
n → n/2 → n/4 → n/8
```

Time complexity:

```txt
O(log n)
```

---

## Constraints Guide

| Input Size | Usually Acceptable |
|---|---|
| `n <= 100` | O(n³) may pass |
| `n <= 1000` | O(n²) may pass |
| `n <= 10⁵` | O(n) or O(n log n) |
| `n <= 10⁶` | O(n) preferred |

---

## Quick Decision Table

| Situation | Think |
|---|---|
| Direct index access | O(1) |
| One full loop | O(n) |
| Nested loops | O(n²) |
| Sorted search | O(log n) |
| Sorting needed | O(n log n) |

---

## Beginner Rule

If `n` is large, avoid unnecessary nested loops.

For optimization, think about:

- Binary Search
- Two Pointers
- HashSet / HashMap
- Sliding Window
- Prefix Sum
- Sorting

---

## Quick Summary

Before finalizing your solution, always check:

```txt
Input size + Time complexity = Can it pass?
```
