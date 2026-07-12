# Pattern 07: HashMap Frequency

HashMap Frequency is an array pattern used when we need to count how many times each element appears.

It is mainly used for:

```txt
frequency counting
occurrence counting
most frequent element
least frequent element
first unique element
two sum lookup
intersection with duplicate counts
```

---

## What Is HashMap?

A `HashMap` stores data in key-value form.

```txt
key   → value
number → frequency
```

Example:

```txt
nums = [2, 3, 2, 4, 3, 2]
```

Frequency map:

```txt
2 → 3
3 → 2
4 → 1
```

This means:

```txt
2 appears 3 times
3 appears 2 times
4 appears 1 time
```

---

## HashSet vs HashMap

HashSet only tells whether a value exists or not.

HashMap tells how many times a value exists.

| Need | Use |
|---|---|
| Check if value exists | HashSet |
| Count frequency | HashMap |
| Track duplicates only | HashSet |
| Track occurrence count | HashMap |
| Store key-value data | HashMap |

Example:

```txt
Need to know if 5 appeared before → HashSet
Need to know how many times 5 appeared → HashMap
```

---

## Java Import

Before using HashMap:

```java
import java.util.HashMap;
```

Create HashMap:

```java
HashMap<Integer, Integer> map = new HashMap<>();
```

Here:

```txt
Integer key   → array element
Integer value → frequency count
```

---

## Important HashMap Methods

| Method | Meaning |
|---|---|
| `map.put(key, value)` | inserts or updates value |
| `map.get(key)` | gets value for key |
| `map.containsKey(key)` | checks if key exists |
| `map.getOrDefault(key, defaultValue)` | gets value, or default if key missing |
| `map.keySet()` | gives all keys |
| `map.size()` | number of unique keys |

---

## Most Important Formula

To count frequency:

```java
map.put(num, map.getOrDefault(num, 0) + 1);
```

Meaning:

```txt
If num already exists → increase its count by 1
If num does not exist → start count from 0, then add 1
```

Example:

```txt
num = 2
old count = 2
new count = 3
```

---

## Pattern Signal

Think of HashMap Frequency when the question says:

```txt
frequency
count occurrence
how many times
most frequent
least frequent
first unique
majority element
same count
duplicate with count
intersection with duplicates
```

Most common signal:

```txt
Count how many times each element appears.
```

---

## Why HashMap Is Needed?

Without HashMap, counting frequency can become slow.

For each element, we may scan the full array again.

That can take:

```txt
O(n²)
```

Using HashMap, we can count all frequencies in one pass.

That usually takes:

```txt
O(n)
```

---

## Basic Logic

```txt
Create empty HashMap
Loop through array
For every element:
    increase its count in map
```

Java:

```java
HashMap<Integer, Integer> map = new HashMap<>();

for (int i = 0; i < nums.length; i++) {
    int num = nums[i];
    map.put(num, map.getOrDefault(num, 0) + 1);
}
```

---

## Complete Java Code: Count Frequency

```java
import java.util.HashMap;

class Solution {
    public HashMap<Integer, Integer> countFrequency(int[] nums) {
        HashMap<Integer, Integer> map = new HashMap<>();

        for (int i = 0; i < nums.length; i++) {
            int num = nums[i];
            map.put(num, map.getOrDefault(num, 0) + 1);
        }

        return map;
    }
}
```

---

## Line-by-Line Explanation

```java
HashMap<Integer, Integer> map = new HashMap<>();
```

Creates an empty HashMap.

---

```java
for (int i = 0; i < nums.length; i++)
```

Traverses every element.

---

```java
int num = nums[i];
```

Stores current element in `num`.

---

```java
map.getOrDefault(num, 0)
```

Gets current count of `num`.

If `num` is not present, it gives `0`.

---

```java
map.put(num, map.getOrDefault(num, 0) + 1);
```

Increases frequency of `num` by 1.

---

```java
return map;
```

Returns the frequency map.

---

## Dry Run: Frequency Count

```txt
nums = [2, 3, 2, 4, 3, 2]
```

Initial map:

```txt
{}
```

| Step | i | nums[i] | Old Count | New Count | Map |
|---:|---:|---:|---:|---:|---|
| 1 | 0 | 2 | 0 | 1 | {2=1} |
| 2 | 1 | 3 | 0 | 1 | {2=1, 3=1} |
| 3 | 2 | 2 | 1 | 2 | {2=2, 3=1} |
| 4 | 3 | 4 | 0 | 1 | {2=2, 3=1, 4=1} |
| 5 | 4 | 3 | 1 | 2 | {2=2, 3=2, 4=1} |
| 6 | 5 | 2 | 2 | 3 | {2=3, 3=2, 4=1} |

Final frequency:

```txt
2 → 3
3 → 2
4 → 1
```

---

## Example 1: Frequency of Target

Problem:

```txt
Find how many times target appears in array.
```

Input:

```txt
nums = [2, 3, 2, 4, 2]
target = 2
```

Output:

```txt
3
```

Code:

```java
import java.util.HashMap;

public int targetFrequency(int[] nums, int target) {
    HashMap<Integer, Integer> map = new HashMap<>();

    for (int i = 0; i < nums.length; i++) {
        map.put(nums[i], map.getOrDefault(nums[i], 0) + 1);
    }

    return map.getOrDefault(target, 0);
}
```

Important:

```txt
If target is not present, return 0.
```

---

## Example 2: Most Frequent Element

Problem:

```txt
Find the element with highest frequency.
```

Input:

```txt
nums = [1, 3, 2, 3, 4, 3]
```

Output:

```txt
3
```

Code:

```java
import java.util.HashMap;

public int mostFrequent(int[] nums) {
    HashMap<Integer, Integer> map = new HashMap<>();

    for (int i = 0; i < nums.length; i++) {
        map.put(nums[i], map.getOrDefault(nums[i], 0) + 1);
    }

    int answer = nums[0];
    int maxFreq = 0;

    for (int key : map.keySet()) {
        int freq = map.get(key);

        if (freq > maxFreq) {
            maxFreq = freq;
            answer = key;
        }
    }

    return answer;
}
```

---

## Example 3: First Unique Element

Problem:

```txt
Return first element that appears only once.
```

Input:

```txt
nums = [4, 5, 1, 2, 1, 5]
```

Output:

```txt
4
```

Code:

```java
import java.util.HashMap;

public int firstUnique(int[] nums) {
    HashMap<Integer, Integer> map = new HashMap<>();

    for (int i = 0; i < nums.length; i++) {
        map.put(nums[i], map.getOrDefault(nums[i], 0) + 1);
    }

    for (int i = 0; i < nums.length; i++) {
        if (map.get(nums[i]) == 1) {
            return nums[i];
        }
    }

    return -1;
}
```

Why second loop?

```txt
HashMap does not preserve original array order.
So we scan original array again to find the first unique element.
```

---

## Example 4: Majority Element

Problem:

```txt
Find element appearing more than n / 2 times.
```

Input:

```txt
nums = [3, 2, 3]
```

Output:

```txt
3
```

Code:

```java
import java.util.HashMap;

public int majorityElement(int[] nums) {
    HashMap<Integer, Integer> map = new HashMap<>();

    for (int i = 0; i < nums.length; i++) {
        map.put(nums[i], map.getOrDefault(nums[i], 0) + 1);

        if (map.get(nums[i]) > nums.length / 2) {
            return nums[i];
        }
    }

    return -1;
}
```

Note:

```txt
This HashMap method is beginner-friendly.
Optimized Boyer-Moore method comes later.
```

---

## Example 5: Two Sum Using HashMap

Problem:

```txt
Return indexes of two numbers whose sum is target.
```

Input:

```txt
nums = [2, 7, 11, 15]
target = 9
```

Output:

```txt
[0, 1]
```

Idea:

```txt
For current number num, need target - num.
If target - num already exists in map, answer found.
Otherwise store num with index.
```

Code:

```java
import java.util.HashMap;

public int[] twoSum(int[] nums, int target) {
    HashMap<Integer, Integer> map = new HashMap<>();

    for (int i = 0; i < nums.length; i++) {
        int need = target - nums[i];

        if (map.containsKey(need)) {
            return new int[]{map.get(need), i};
        }

        map.put(nums[i], i);
    }

    return new int[]{-1, -1};
}
```

Important:

```txt
HashMap stores value → index
```

This is not frequency counting, but it is a very common HashMap array pattern.

---

## Example 6: Intersection With Duplicate Counts

Problem:

```txt
Return intersection of two arrays including duplicates.
```

Input:

```txt
nums1 = [1, 2, 2, 3]
nums2 = [2, 2, 4]
```

Output:

```txt
[2, 2]
```

Idea:

```txt
Count frequency of nums1.
Scan nums2.
If frequency exists, add to result and decrease frequency.
```

Code:

```java
import java.util.HashMap;
import java.util.ArrayList;

public int[] intersect(int[] nums1, int[] nums2) {
    HashMap<Integer, Integer> map = new HashMap<>();

    for (int i = 0; i < nums1.length; i++) {
        map.put(nums1[i], map.getOrDefault(nums1[i], 0) + 1);
    }

    ArrayList<Integer> list = new ArrayList<>();

    for (int i = 0; i < nums2.length; i++) {
        int num = nums2[i];

        if (map.getOrDefault(num, 0) > 0) {
            list.add(num);
            map.put(num, map.get(num) - 1);
        }
    }

    int[] result = new int[list.size()];

    for (int i = 0; i < list.size(); i++) {
        result[i] = list.get(i);
    }

    return result;
}
```

---

## Time and Space Complexity

For frequency counting:

| Complexity | Value |
|---|---:|
| Time Complexity | O(n) average |
| Space Complexity | O(n) |

Why time is O(n)?

```txt
We scan array once.
HashMap put/get operations are O(1) on average.
```

Why space is O(n)?

```txt
In worst case, all elements are unique and stored as keys.
```

---

## HashMap Frequency vs Prefix Sum HashMap

HashMap Frequency is for counting values.

Example:

```txt
How many times did 5 appear?
```

Prefix Sum HashMap is for subarray sum problems.

Example:

```txt
How many subarrays have sum k?
```

Prefix Sum + HashMap will be covered later as a separate pattern.

---

## Common Mistakes

### 1. Forgetting Import

Correct:

```java
import java.util.HashMap;
```

---

### 2. Using `get()` Without Checking

Wrong:

```java
map.put(num, map.get(num) + 1);
```

If `num` is not present, `map.get(num)` gives `null`.

Correct:

```java
map.put(num, map.getOrDefault(num, 0) + 1);
```

---

### 3. Using HashSet When Frequency Is Needed

Wrong pattern:

```txt
HashSet
```

Correct pattern:

```txt
HashMap
```

Because HashSet cannot store counts.

---

### 4. Depending on HashMap Order

HashMap does not guarantee sorted order or insertion order.

If order matters, scan the original array again.

Example:

```txt
First unique element
```

---

### 5. Forgetting to Decrease Frequency

In intersection with duplicates:

```java
map.put(num, map.get(num) - 1);
```

This is important.

Otherwise same element may be used more times than allowed.

---

## Beginner Checklist

Before applying HashMap Frequency, ask:

```txt
1. Do I need to count occurrences?
2. Do I need frequency of each value?
3. Do I need most frequent or least frequent?
4. Do I need first unique element?
5. Do I need value → index mapping?
6. Should I use getOrDefault?
7. Does order matter?
8. Should I scan original array again?
9. Is this frequency problem or prefix-sum problem?
```

---

## Pattern Summary

| Point | Meaning |
|---|---|
| Pattern Name | HashMap Frequency |
| Pattern Number | 07 |
| Used For | Frequency, counts, value-index lookup |
| Main Method | `getOrDefault()` |
| Update Formula | `map.put(x, map.getOrDefault(x, 0) + 1)` |
| Time | O(n) average |
| Space | O(n) |
| If only existence needed | Use HashSet |
| If subarray sum needed | Prefix Sum + HashMap later |

---

## Next Pattern

```txt
Pattern 08: Sorting-Based Patterns
```
