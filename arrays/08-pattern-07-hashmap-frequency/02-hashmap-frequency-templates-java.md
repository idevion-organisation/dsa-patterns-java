# HashMap Frequency Templates in Java

This file contains common HashMap templates used in array problems.

Use these templates when the problem asks for frequency, occurrence count, value-index lookup, or duplicate count handling.

---

## Required Import

```java
import java.util.HashMap;
```

---

## Template 1: Build Frequency Map

Use when question asks:

```txt
Count frequency of every element.
```

Code:

```java
public HashMap<Integer, Integer> buildFrequencyMap(int[] nums) {
    HashMap<Integer, Integer> map = new HashMap<>();

    for (int i = 0; i < nums.length; i++) {
        map.put(nums[i], map.getOrDefault(nums[i], 0) + 1);
    }

    return map;
}
```

---

## Template 2: Frequency of Target

Use when question asks:

```txt
How many times does target appear?
```

Code:

```java
public int targetFrequency(int[] nums, int target) {
    HashMap<Integer, Integer> map = new HashMap<>();

    for (int i = 0; i < nums.length; i++) {
        map.put(nums[i], map.getOrDefault(nums[i], 0) + 1);
    }

    return map.getOrDefault(target, 0);
}
```

---

## Template 3: Most Frequent Element

Use when question asks:

```txt
Find element with highest frequency.
```

Code:

```java
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

## Template 4: First Unique Element

Use when question asks:

```txt
Return first element that appears once.
```

Code:

```java
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

Why scan original array again?

```txt
Because HashMap does not preserve original order.
```

---

## Template 5: Majority Element

Use when question asks:

```txt
Find element appearing more than n / 2 times.
```

Code:

```java
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

---

## Template 6: Two Sum Using HashMap

Use when question asks:

```txt
Return indexes of two numbers whose sum is target.
```

Code:

```java
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

HashMap stores:

```txt
value → index
```

---

## Template 7: Intersection With Duplicate Counts

Use when question asks:

```txt
Intersection of arrays including duplicates.
```

Code:

```java
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

## Template 8: Same Frequency Check

Use when question asks:

```txt
Check if two arrays have the same frequency of elements.
```

Code:

```java
public boolean sameFrequency(int[] a, int[] b) {
    if (a.length != b.length) {
        return false;
    }

    HashMap<Integer, Integer> map = new HashMap<>();

    for (int i = 0; i < a.length; i++) {
        map.put(a[i], map.getOrDefault(a[i], 0) + 1);
    }

    for (int i = 0; i < b.length; i++) {
        if (!map.containsKey(b[i])) {
            return false;
        }

        map.put(b[i], map.get(b[i]) - 1);

        if (map.get(b[i]) == 0) {
            map.remove(b[i]);
        }
    }

    return map.isEmpty();
}
```

---

## Template Selection Table

| Requirement | Template |
|---|---|
| Count all values | Build Frequency Map |
| Count target | Frequency of Target |
| Most frequent value | Most Frequent Element |
| First unique value | First Unique Element |
| Majority element | Majority Element |
| Two Sum indexes | Two Sum Using HashMap |
| Intersection with duplicates | Intersection With Counts |
| Compare two arrays by frequency | Same Frequency Check |

---

## How to Decide Which Template to Use?

Ask:

```txt
What should key and value represent?
```

| Problem Type | Key | Value |
|---|---|---|
| Frequency count | number | count |
| Two Sum | number | index |
| Intersection count | number | remaining count |
| Same frequency | number | count difference |
| First unique | number | count |

---

## Beginner Rule

HashMap is not only for counting.

It stores:

```txt
key → value
```

So always decide:

```txt
What should be my key?
What should be my value?
```

For frequency problems:

```txt
key = array element
value = count
```
