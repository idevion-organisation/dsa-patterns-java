# Merge Sorted Arrays Templates in Java

This file contains common templates for Merge Sorted Arrays pattern.

Use these templates when the problem gives sorted arrays and asks you to merge, combine, compare, or find common elements.

---

## Template 1: Merge Two Sorted Arrays Into New Array

Use when question asks:

```txt
Merge two sorted arrays and return a new sorted array.
```

Code:

```java
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
```

Time:

```txt
O(m + n)
```

Space:

```txt
O(m + n)
```

---

## Template 2: Merge nums2 Into nums1 In-place

Use when question asks:

```txt
nums1 has extra space at the end.
Merge nums2 into nums1 in sorted order.
```

Code:

```java
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
```

Why from end?

```txt
To avoid overwriting valid nums1 elements.
```

Time:

```txt
O(m + n)
```

Space:

```txt
O(1)
```

---

## Template 3: Merge Unique Elements from Two Sorted Arrays

Use when question asks:

```txt
Merge two sorted arrays but keep each value only once.
```

Code:

```java
import java.util.ArrayList;

public int[] mergeUnique(int[] a, int[] b) {
    ArrayList<Integer> list = new ArrayList<>();

    int i = 0;
    int j = 0;

    while (i < a.length && j < b.length) {
        int value;

        if (a[i] < b[j]) {
            value = a[i];
            i++;
        }
        else if (a[i] > b[j]) {
            value = b[j];
            j++;
        }
        else {
            value = a[i];
            i++;
            j++;
        }

        if (list.size() == 0 || list.get(list.size() - 1) != value) {
            list.add(value);
        }
    }

    while (i < a.length) {
        if (list.size() == 0 || list.get(list.size() - 1) != a[i]) {
            list.add(a[i]);
        }
        i++;
    }

    while (j < b.length) {
        if (list.size() == 0 || list.get(list.size() - 1) != b[j]) {
            list.add(b[j]);
        }
        j++;
    }

    int[] result = new int[list.size()];

    for (int k = 0; k < list.size(); k++) {
        result[k] = list.get(k);
    }

    return result;
}
```

---

## Template 4: Intersection of Two Sorted Arrays With Duplicates

Use when question asks:

```txt
Return common elements.
Duplicates should be included.
```

Example:

```txt
a = [1, 2, 2, 3]
b = [2, 2, 4]
```

Output:

```txt
[2, 2]
```

Code:

```java
import java.util.ArrayList;

public int[] intersectionWithDuplicates(int[] a, int[] b) {
    ArrayList<Integer> list = new ArrayList<>();

    int i = 0;
    int j = 0;

    while (i < a.length && j < b.length) {
        if (a[i] == b[j]) {
            list.add(a[i]);
            i++;
            j++;
        }
        else if (a[i] < b[j]) {
            i++;
        }
        else {
            j++;
        }
    }

    int[] result = new int[list.size()];

    for (int k = 0; k < list.size(); k++) {
        result[k] = list.get(k);
    }

    return result;
}
```

---

## Template 5: Intersection of Two Sorted Arrays Unique

Use when question asks:

```txt
Return common elements only once.
```

Code:

```java
import java.util.ArrayList;

public int[] intersectionUnique(int[] a, int[] b) {
    ArrayList<Integer> list = new ArrayList<>();

    int i = 0;
    int j = 0;

    while (i < a.length && j < b.length) {
        if (a[i] == b[j]) {
            if (list.size() == 0 || list.get(list.size() - 1) != a[i]) {
                list.add(a[i]);
            }

            int value = a[i];

            while (i < a.length && a[i] == value) {
                i++;
            }

            while (j < b.length && b[j] == value) {
                j++;
            }
        }
        else if (a[i] < b[j]) {
            i++;
        }
        else {
            j++;
        }
    }

    int[] result = new int[list.size()];

    for (int k = 0; k < list.size(); k++) {
        result[k] = list.get(k);
    }

    return result;
}
```

---

## Template 6: Union of Two Sorted Arrays

Use when question asks:

```txt
Return all unique values from both sorted arrays.
```

This is similar to merge unique.

Code:

```java
import java.util.ArrayList;

public int[] unionSortedArrays(int[] a, int[] b) {
    ArrayList<Integer> list = new ArrayList<>();

    int i = 0;
    int j = 0;

    while (i < a.length && j < b.length) {
        int value;

        if (a[i] < b[j]) {
            value = a[i];
            i++;
        }
        else if (a[i] > b[j]) {
            value = b[j];
            j++;
        }
        else {
            value = a[i];
            i++;
            j++;
        }

        if (list.size() == 0 || list.get(list.size() - 1) != value) {
            list.add(value);
        }
    }

    while (i < a.length) {
        if (list.size() == 0 || list.get(list.size() - 1) != a[i]) {
            list.add(a[i]);
        }
        i++;
    }

    while (j < b.length) {
        if (list.size() == 0 || list.get(list.size() - 1) != b[j]) {
            list.add(b[j]);
        }
        j++;
    }

    int[] result = new int[list.size()];

    for (int k = 0; k < list.size(); k++) {
        result[k] = list.get(k);
    }

    return result;
}
```

---

## Template 7: Median After Merging Two Sorted Arrays

Use when question asks:

```txt
Find median of two sorted arrays.
```

Beginner-friendly method:

```txt
Merge first, then find median.
```

Code:

```java
public double findMedianSortedArrays(int[] a, int[] b) {
    int[] merged = mergeSortedArrays(a, b);

    int n = merged.length;

    if (n % 2 == 1) {
        return merged[n / 2];
    }

    int mid1 = merged[n / 2 - 1];
    int mid2 = merged[n / 2];

    return (mid1 + mid2) / 2.0;
}

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
```

Note:

```txt
This is beginner-friendly.
There is a more optimized binary search method, but that is advanced.
```

---

## Template Selection Table

| Requirement | Template |
|---|---|
| Return merged sorted array | Merge Into New Array |
| Merge nums2 into nums1 | In-place Merge From End |
| Merge without duplicates | Merge Unique |
| Common elements with duplicates | Intersection With Duplicates |
| Common elements once | Intersection Unique |
| All unique values from both arrays | Union Sorted Arrays |
| Median of two sorted arrays | Merge + Median |

---

## How to Decide Which Template to Use?

Ask:

```txt
What type of merge does the question want?
```

| Question Wants | Use |
|---|---|
| All elements | Normal merge |
| All elements in nums1 | In-place merge |
| Only unique elements | Merge unique |
| Only common elements | Intersection |
| Common elements with repeated count | Intersection with duplicates |
| All unique elements from both arrays | Union |
| Middle value after merge | Median after merge |

---

## Beginner Rule

Merge Sorted Arrays pattern depends on one simple idea:

```txt
Both arrays are already sorted,
so compare current elements and move the correct pointer.
```

For normal merge:

```txt
Pick smaller from front.
```

For in-place merge:

```txt
Pick larger from end.
```
