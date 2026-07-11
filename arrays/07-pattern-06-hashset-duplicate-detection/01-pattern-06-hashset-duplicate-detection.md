# Pattern 06: HashSet / Duplicate Detection

HashSet is an important array pattern used when we need to check whether an element has already appeared before.

It is mostly used for:

```txt
duplicates
unique elements
visited elements
existence checking
set operations
```

---

## What Is HashSet?

A `HashSet` is a collection that stores only unique values.

It does not allow duplicate values.

Example:

```java
HashSet<Integer> set = new HashSet<>();

set.add(10);
set.add(20);
set.add(10);
```

Final set:

```txt
[10, 20]
```

The second `10` is ignored because `10` already exists.

---

## Why HashSet Is Useful?

Without HashSet, to check duplicate elements, we may compare every element with every other element.

That takes:

```txt
O(n²)
```

With HashSet, we can check if an element already exists in almost constant time.

That usually takes:

```txt
O(n)
```

---

## Simple Meaning

```txt
Read each element
Check if it was already seen
If yes → duplicate found
If no → store it in HashSet
```

---

## Java Import

Before using HashSet, write:

```java
import java.util.HashSet;
```

Usually we write:

```java
HashSet<Integer> set = new HashSet<>();
```

---

## Important HashSet Methods

| Method | Meaning |
|---|---|
| `set.add(x)` | adds `x` to set |
| `set.contains(x)` | checks if `x` exists |
| `set.remove(x)` | removes `x` |
| `set.size()` | returns number of unique elements |
| `set.isEmpty()` | checks if set is empty |

---

## Pattern Signal

Think of HashSet when the question says:

```txt
duplicate
unique
already seen
visited
exists before
common elements
intersection
distinct elements
repeated element
```

Most common signal:

```txt
Check if duplicate exists
```

---

## HashSet vs Traversal

| Point | Traversal | HashSet |
|---|---|---|
| Main use | Visit every element | Track seen elements |
| Duplicate check | Needs nested loop | Easy with `contains()` |
| Time for duplicate check | O(n²) | O(n) average |
| Extra space | O(1) | O(n) |

HashSet improves time but uses extra space.

---

## Brute Force Duplicate Check

Problem:

```txt
Check if array contains duplicate.
```

Input:

```txt
nums = [1, 2, 3, 1]
```

Brute force idea:

```txt
Compare every pair.
```

Code:

```java
public boolean containsDuplicate(int[] nums) {
    for (int i = 0; i < nums.length; i++) {
        for (int j = i + 1; j < nums.length; j++) {
            if (nums[i] == nums[j]) {
                return true;
            }
        }
    }

    return false;
}
```

Time:

```txt
O(n²)
```

This is simple but slow for large input.

---

## Optimized Idea Using HashSet

Use HashSet to remember visited elements.

For each element:

```txt
If element already exists in set → duplicate found
Else add element to set
```

---

## Complete Java Code: Contains Duplicate

```java
import java.util.HashSet;

class Solution {
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
}
```

---

## Line-by-Line Explanation

```java
HashSet<Integer> set = new HashSet<>();
```

Creates an empty set to store already seen numbers.

---

```java
for (int i = 0; i < nums.length; i++)
```

Checks each element one by one.

---

```java
if (set.contains(nums[i]))
```

Checks whether current element already exists in set.

---

```java
return true;
```

If current element is already present, duplicate exists.

---

```java
set.add(nums[i]);
```

If element is not already present, store it in set.

---

```java
return false;
```

If loop ends and no duplicate is found, return false.

---

## Dry Run: Duplicate Found

```txt
nums = [1, 2, 3, 1]
```

Initial set:

```txt
{}
```

| Step | i | nums[i] | Already in set? | Action | Set |
|---:|---:|---:|---|---|---|
| 1 | 0 | 1 | No | add 1 | {1} |
| 2 | 1 | 2 | No | add 2 | {1, 2} |
| 3 | 2 | 3 | No | add 3 | {1, 2, 3} |
| 4 | 3 | 1 | Yes | duplicate found | {1, 2, 3} |

Answer:

```txt
true
```

---

## Dry Run: No Duplicate

```txt
nums = [1, 2, 3, 4]
```

| Step | i | nums[i] | Already in set? | Action | Set |
|---:|---:|---:|---|---|---|
| 1 | 0 | 1 | No | add 1 | {1} |
| 2 | 1 | 2 | No | add 2 | {1, 2} |
| 3 | 2 | 3 | No | add 3 | {1, 2, 3} |
| 4 | 3 | 4 | No | add 4 | {1, 2, 3, 4} |

No duplicate found.

Answer:

```txt
false
```

---

## Important Note About Order

HashSet does not guarantee insertion order.

Example:

```java
HashSet<Integer> set = new HashSet<>();
set.add(3);
set.add(1);
set.add(2);

System.out.println(set);
```

Output may not be:

```txt
[3, 1, 2]
```

So do not use HashSet when order matters.

Use HashSet mainly for:

```txt
existence checking
duplicate detection
unique values
```

---

## Example 1: Count Unique Elements

Problem:

```txt
Count how many unique elements are present.
```

Input:

```txt
nums = [1, 2, 2, 3, 1]
```

Output:

```txt
3
```

Unique elements:

```txt
1, 2, 3
```

Code:

```java
import java.util.HashSet;

public int countUnique(int[] nums) {
    HashSet<Integer> set = new HashSet<>();

    for (int i = 0; i < nums.length; i++) {
        set.add(nums[i]);
    }

    return set.size();
}
```

---

## Example 2: Print Unique Elements

Problem:

```txt
Print each unique element once.
```

Code:

```java
import java.util.HashSet;

public void printUnique(int[] nums) {
    HashSet<Integer> set = new HashSet<>();

    for (int i = 0; i < nums.length; i++) {
        set.add(nums[i]);
    }

    for (int value : set) {
        System.out.println(value);
    }
}
```

Important:

```txt
Printing order may be different because HashSet is unordered.
```

---

## Example 3: Intersection of Two Arrays

Problem:

```txt
Return common unique elements from two arrays.
```

Input:

```txt
nums1 = [1, 2, 2, 3]
nums2 = [2, 2, 4]
```

Output:

```txt
[2]
```

Code:

```java
import java.util.HashSet;
import java.util.ArrayList;

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

Why use `resultSet`?

```txt
Because output should contain unique common elements.
```

---

## Example 4: Find First Repeated Element

Problem:

```txt
Return the first value that repeats while scanning from left to right.
```

Input:

```txt
nums = [5, 1, 3, 1, 5]
```

Output:

```txt
1
```

Code:

```java
import java.util.HashSet;

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

Explanation:

```txt
1 repeats first during left-to-right scanning.
```

---

## Example 5: Check If Two Arrays Have Common Element

Problem:

```txt
Check if two arrays have at least one common element.
```

Code:

```java
import java.util.HashSet;

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

## Example 6: Longest Consecutive Sequence

This is a medium-level HashSet problem.

Problem:

```txt
Find length of longest consecutive sequence.
```

Input:

```txt
nums = [100, 4, 200, 1, 3, 2]
```

Output:

```txt
4
```

Because:

```txt
1, 2, 3, 4
```

Idea:

```txt
Store all numbers in HashSet.
Start a sequence only if num - 1 is not present.
Count num, num + 1, num + 2...
```

Code:

```java
import java.util.HashSet;

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

Why check:

```java
!set.contains(num - 1)
```

Because we only start counting from the beginning of a sequence.

Example:

```txt
1 starts sequence 1,2,3,4
2 should not start again
3 should not start again
4 should not start again
```

---

## Time and Space Complexity

For duplicate detection:

| Complexity | Value |
|---|---:|
| Time Complexity | O(n) average |
| Space Complexity | O(n) |

Why time is O(n)?

```txt
We scan every element once.
HashSet contains/add are O(1) on average.
```

Why space is O(n)?

```txt
In worst case, all elements are unique and stored in set.
```

---

## Common Mistakes

### 1. Forgetting Import

Wrong:

```java
HashSet<Integer> set = new HashSet<>();
```

without import.

Correct:

```java
import java.util.HashSet;
```

---

### 2. Adding Before Checking Duplicate

Wrong:

```java
set.add(nums[i]);

if (set.contains(nums[i])) {
    return true;
}
```

This will always become true after adding.

Correct:

```java
if (set.contains(nums[i])) {
    return true;
}

set.add(nums[i]);
```

---

### 3. Thinking HashSet Stores Duplicates

HashSet stores only unique values.

If you need frequency, use:

```txt
HashMap
```

HashMap will be covered in the next pattern.

---

### 4. Expecting Sorted Order

HashSet does not sort values.

If sorted order is needed, use sorting or another structure.

---

### 5. Using HashSet When Index Is Important

HashSet stores values, not indexes.

If question asks:

```txt
same value within distance k
index difference
position tracking
```

You may need HashMap or sliding window with HashSet.

---

## Beginner Checklist

Before applying HashSet, ask:

```txt
1. Do I need to check if something already appeared?
2. Do I need only unique values?
3. Do I need duplicate detection?
4. Is frequency required?
5. Is index required?
6. Does order matter?
7. Can I trade extra space O(n) for faster time O(n)?
8. Should I check before adding?
```

---

## Pattern Summary

| Point | Meaning |
|---|---|
| Pattern Name | HashSet / Duplicate Detection |
| Pattern Number | 06 |
| Used For | Duplicates, unique values, existence checking |
| Main Method | `contains()` |
| Add Method | `add()` |
| Time | O(n) average |
| Space | O(n) |
| Order Maintained? | No |
| If frequency needed | Use HashMap |

---

## Next Pattern

```txt
Pattern 07: HashMap Frequency
```
