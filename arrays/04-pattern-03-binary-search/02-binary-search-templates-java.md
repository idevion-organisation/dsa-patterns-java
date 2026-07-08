# Binary Search Templates in Java

This file contains common Binary Search templates in Java.

Use these templates when the problem is based on a sorted array or sorted search space.

---

## Template 1: Return Index of Target

Use when question asks:

```txt
Return index of target.
Return -1 if target is not found.
```

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

## Template 2: Return True or False

Use when question asks:

```txt
Check whether target exists or not.
```

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

## Template 3: Search Insert Position

Use when question asks:

```txt
Return index if target exists.
Otherwise return where target should be inserted.
```

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

Important:

```txt
When loop ends, left is the insertion position.
```

---

## Template 4: First Occurrence

Use when:

```txt
Array is sorted.
Array has duplicate values.
Question asks for first index of target.
```

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

Why?

```txt
Store current index and continue searching on the left side.
```

---

## Template 5: Last Occurrence

Use when:

```txt
Array is sorted.
Array has duplicate values.
Question asks for last index of target.
```

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

Why?

```txt
Store current index and continue searching on the right side.
```

---

## Template 6: Lower Bound

Lower bound means:

```txt
First index where nums[index] >= target
```

Example:

```txt
nums = [1, 3, 3, 5, 7]
target = 3
```

Answer:

```txt
1
```

```java
public int lowerBound(int[] nums, int target) {
    int left = 0;
    int right = nums.length;

    while (left < right) {
        int mid = left + (right - left) / 2;

        if (nums[mid] >= target) {
            right = mid;
        }
        else {
            left = mid + 1;
        }
    }

    return left;
}
```

---

## Template 7: Upper Bound

Upper bound means:

```txt
First index where nums[index] > target
```

Example:

```txt
nums = [1, 3, 3, 5, 7]
target = 3
```

Answer:

```txt
3
```

```java
public int upperBound(int[] nums, int target) {
    int left = 0;
    int right = nums.length;

    while (left < right) {
        int mid = left + (right - left) / 2;

        if (nums[mid] > target) {
            right = mid;
        }
        else {
            left = mid + 1;
        }
    }

    return left;
}
```

---

## Template Selection Table

| Requirement | Template |
|---|---|
| Return target index | Basic Binary Search |
| Return true/false | Boolean Binary Search |
| Return insert position | Search Insert Position |
| Find first target index | First Occurrence |
| Find last target index | Last Occurrence |
| First index `>= target` | Lower Bound |
| First index `> target` | Upper Bound |

---

## How to Decide Which Template to Use?

Ask:

```txt
What does the question want after finding the middle?
```

| Question Wants | Action |
|---|---|
| Any target index | return `mid` |
| First occurrence | store `mid`, move left |
| Last occurrence | store `mid`, move right |
| Insert position | return `left` after loop |
| First `>= target` | lower bound |
| First `> target` | upper bound |

---

## Beginner Rule

Start with the basic template:

```java
while (left <= right)
```

Then learn special cases:

```txt
first occurrence
last occurrence
search insert position
lower bound
upper bound
```

The main skill is understanding:

```txt
How should left and right move?
```
