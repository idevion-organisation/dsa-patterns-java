# HashSet Templates in Java

This file contains common HashSet templates in Java.

Use these templates when the problem asks about duplicates, unique values, visited elements, or existence checking.

---

## Required Import

```java
import java.util.HashSet;
```

---

## Template 1: Contains Duplicate

Use when question asks:

```txt
Check if any duplicate exists.
```

Code:

```java
public boolean containsDuplicate(int[] nums) {
    HashSet<Integer> set = new HashSet<>();

    for (int i = 0; i < nums.length; i++) {
        if (set.contains(nums[i])) {
            return true;
        }

        set.add(nums[i]);
    }

    return false;
}
```

---

## Template 2: Count Unique Elements

Use when question asks:

```txt
Count distinct or unique elements.
```

Code:

```java
public int countUnique(int[] nums) {
    HashSet<Integer> set = new HashSet<>();

    for (int i = 0; i < nums.length; i++) {
        set.add(nums[i]);
    }

    return set.size();
}
```

---

## Template 3: First Repeated Value

Use when question asks:

```txt
Return first value that repeats while scanning left to right.
```

Code:

```java
public int firstRepeatedValue(int[] nums) {
    HashSet<Integer> set = new HashSet<>();

    for (int i = 0; i < nums.length; i++) {
        if (set.contains(nums[i])) {
            return nums[i];
        }

        set.add(nums[i]);
    }

    return -1;
}
```

---

## Template 4: Unique Elements Array

Use when question asks:

```txt
Return all unique elements.
```

Code:

```java
public int[] uniqueElements(int[] nums) {
    HashSet<Integer> set = new HashSet<>();

    for (int i = 0; i < nums.length; i++) {
        set.add(nums[i]);
    }

    int[] result = new int[set.size()];
    int index = 0;

    for (int value : set) {
        result[index] = value;
        index++;
    }

    return result;
}
```

Important:

```txt
Order is not guaranteed.
```

---

## Template 5: Intersection of Two Arrays

Use when question asks:

```txt
Return common unique elements from two arrays.
```

Code:

```java
import java.util.HashSet;

public int[] intersection(int[] nums1, int[] nums2) {
    HashSet<Integer> set1 = new HashSet<>();
    HashSet<Integer> resultSet = new HashSet<>();

    for (int i = 0; i < nums1.length; i++) {
        set1.add(nums1[i]);
    }

    for (int i = 0; i < nums2.length; i++) {
        if (set1.contains(nums2[i])) {
            resultSet.add(nums2[i]);
        }
    }

    int[] result = new int[resultSet.size()];
    int index = 0;

    for (int value : resultSet) {
        result[index] = value;
        index++;
    }

    return result;
}
```

---

## Template 6: Check Common Element

Use when question asks:

```txt
Do two arrays have at least one common element?
```

Code:

```java
public boolean hasCommonElement(int[] nums1, int[] nums2) {
    HashSet<Integer> set = new HashSet<>();

    for (int i = 0; i < nums1.length; i++) {
        set.add(nums1[i]);
    }

    for (int i = 0; i < nums2.length; i++) {
        if (set.contains(nums2[i])) {
            return true;
        }
    }

    return false;
}
```

---

## Template 7: Missing Number Using HashSet

Use when question asks:

```txt
Find missing number from range 0 to n.
```

Example:

```txt
nums = [3, 0, 1]
```

Output:

```txt
2
```

Code:

```java
public int missingNumber(int[] nums) {
    HashSet<Integer> set = new HashSet<>();

    for (int i = 0; i < nums.length; i++) {
        set.add(nums[i]);
    }

    for (int i = 0; i <= nums.length; i++) {
        if (!set.contains(i)) {
            return i;
        }
    }

    return -1;
}
```

Note:

```txt
This is easy to understand.
More optimized math/XOR methods come later.
```

---

## Template 8: Longest Consecutive Sequence

Use when question asks:

```txt
Find longest sequence of consecutive numbers.
```

Code:

```java
public int longestConsecutive(int[] nums) {
    HashSet<Integer> set = new HashSet<>();

    for (int i = 0; i < nums.length; i++) {
        set.add(nums[i]);
    }

    int longest = 0;

    for (int num : set) {
        if (!set.contains(num - 1)) {
            int current = num;
            int length = 1;

            while (set.contains(current + 1)) {
                current++;
                length++;
            }

            if (length > longest) {
                longest = length;
            }
        }
    }

    return longest;
}
```

---

## Template Selection Table

| Requirement | Template |
|---|---|
| Check duplicate exists | Contains Duplicate |
| Count unique values | Count Unique |
| First repeated value | First Repeated Value |
| Return unique values | Unique Elements Array |
| Common unique elements | Intersection |
| Check common element | Common Element |
| Missing number | Missing Number Using HashSet |
| Consecutive sequence | Longest Consecutive Sequence |

---

## How to Decide Which Template to Use?

Ask:

```txt
What do I need to know about the element?
```

| Question Need | HashSet Use |
|---|---|
| Already appeared? | `contains()` before `add()` |
| Store unique values? | `add()` |
| Count unique values? | `set.size()` |
| Common values? | build set from one array, check second |
| Missing from range? | store all, check range |
| Consecutive sequence? | check `num - 1` and `num + 1` |

---

## Beginner Rule

HashSet is best when the question is about:

```txt
Have I seen this value before?
```

If the question asks:

```txt
How many times did this value appear?
```

Then use:

```txt
HashMap
```
