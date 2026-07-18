# Prefix Sum + HashMap Templates in Java

This file contains common Prefix Sum + HashMap templates for subarray sum problems.

Use these templates when the problem asks about subarray sum equal to target, zero sum subarray, count of subarrays, or longest subarray with sum k.

---

## Required Imports

For HashMap:

```java
import java.util.HashMap;
```

For HashSet:

```java
import java.util.HashSet;
```

---

## Template 1: Count Subarrays With Sum K

Use when question asks:

```txt
Count number of subarrays whose sum equals k.
```

Code:

```java
import java.util.HashMap;

public int subarraySum(int[] nums, int k) {
    HashMap<Integer, Integer> map = new HashMap<>();

    map.put(0, 1);

    int currentSum = 0;
    int count = 0;

    for (int i = 0; i < nums.length; i++) {
        currentSum += nums[i];

        int need = currentSum - k;

        count += map.getOrDefault(need, 0);

        map.put(currentSum, map.getOrDefault(currentSum, 0) + 1);
    }

    return count;
}
```

HashMap stores:

```txt
prefix sum → frequency
```

---

## Template 2: Check If Subarray With Sum K Exists

Use when question asks:

```txt
Return true if any subarray has sum k.
```

Code:

```java
import java.util.HashSet;

public boolean hasSubarraySumK(int[] nums, int k) {
    HashSet<Integer> set = new HashSet<>();

    set.add(0);

    int currentSum = 0;

    for (int i = 0; i < nums.length; i++) {
        currentSum += nums[i];

        int need = currentSum - k;

        if (set.contains(need)) {
            return true;
        }

        set.add(currentSum);
    }

    return false;
}
```

HashSet is enough because we only check existence.

---

## Template 3: Longest Subarray With Sum K

Use when question asks:

```txt
Find maximum length subarray whose sum equals k.
```

Code:

```java
import java.util.HashMap;

public int longestSubarraySumK(int[] nums, int k) {
    HashMap<Integer, Integer> map = new HashMap<>();

    map.put(0, -1);

    int currentSum = 0;
    int maxLength = 0;

    for (int i = 0; i < nums.length; i++) {
        currentSum += nums[i];

        int need = currentSum - k;

        if (map.containsKey(need)) {
            int length = i - map.get(need);

            if (length > maxLength) {
                maxLength = length;
            }
        }

        if (!map.containsKey(currentSum)) {
            map.put(currentSum, i);
        }
    }

    return maxLength;
}
```

HashMap stores:

```txt
prefix sum → first index
```

---

## Template 4: Check Zero Sum Subarray

Use when question asks:

```txt
Return true if any subarray has sum 0.
```

Code:

```java
import java.util.HashSet;

public boolean hasZeroSumSubarray(int[] nums) {
    HashSet<Integer> set = new HashSet<>();

    set.add(0);

    int currentSum = 0;

    for (int i = 0; i < nums.length; i++) {
        currentSum += nums[i];

        if (set.contains(currentSum)) {
            return true;
        }

        set.add(currentSum);
    }

    return false;
}
```

Why it works:

```txt
If same prefix sum appears twice, the subarray between them has sum 0.
```

---

## Template 5: Count Zero Sum Subarrays

Use when question asks:

```txt
Count subarrays whose sum is 0.
```

Code:

```java
import java.util.HashMap;

public int countZeroSumSubarrays(int[] nums) {
    HashMap<Integer, Integer> map = new HashMap<>();

    map.put(0, 1);

    int currentSum = 0;
    int count = 0;

    for (int i = 0; i < nums.length; i++) {
        currentSum += nums[i];

        count += map.getOrDefault(currentSum, 0);

        map.put(currentSum, map.getOrDefault(currentSum, 0) + 1);
    }

    return count;
}
```

This is same as:

```txt
count subarrays with sum k
```

where:

```txt
k = 0
```

---

## Template 6: Longest Zero Sum Subarray

Use when question asks:

```txt
Find length of longest subarray with sum 0.
```

Code:

```java
import java.util.HashMap;

public int longestZeroSumSubarray(int[] nums) {
    HashMap<Integer, Integer> map = new HashMap<>();

    map.put(0, -1);

    int currentSum = 0;
    int maxLength = 0;

    for (int i = 0; i < nums.length; i++) {
        currentSum += nums[i];

        if (map.containsKey(currentSum)) {
            int length = i - map.get(currentSum);

            if (length > maxLength) {
                maxLength = length;
            }
        }
        else {
            map.put(currentSum, i);
        }
    }

    return maxLength;
}
```

---

## Template 7: Equal Number of 0s and 1s

Use when question asks:

```txt
Find longest subarray with equal number of 0s and 1s.
```

Code:

```java
import java.util.HashMap;

public int findMaxLength(int[] nums) {
    HashMap<Integer, Integer> map = new HashMap<>();

    map.put(0, -1);

    int currentSum = 0;
    int maxLength = 0;

    for (int i = 0; i < nums.length; i++) {
        if (nums[i] == 0) {
            currentSum += -1;
        }
        else {
            currentSum += 1;
        }

        if (map.containsKey(currentSum)) {
            int length = i - map.get(currentSum);

            if (length > maxLength) {
                maxLength = length;
            }
        }
        else {
            map.put(currentSum, i);
        }
    }

    return maxLength;
}
```

Trick:

```txt
0 becomes -1
1 remains +1
```

Then equal 0s and 1s means:

```txt
subarray sum = 0
```

---

## Template 8: Count Subarrays Divisible by K

Use when question asks:

```txt
Count subarrays whose sum is divisible by k.
```

Code:

```java
import java.util.HashMap;

public int subarraysDivByK(int[] nums, int k) {
    HashMap<Integer, Integer> map = new HashMap<>();

    map.put(0, 1);

    int currentSum = 0;
    int count = 0;

    for (int i = 0; i < nums.length; i++) {
        currentSum += nums[i];

        int remainder = currentSum % k;

        if (remainder < 0) {
            remainder += k;
        }

        count += map.getOrDefault(remainder, 0);

        map.put(remainder, map.getOrDefault(remainder, 0) + 1);
    }

    return count;
}
```

Idea:

```txt
If two prefix sums have same remainder,
their difference is divisible by k.
```

---

## Template Selection Table

| Requirement | Template |
|---|---|
| Count subarrays with sum k | Count Subarrays With Sum K |
| Check if sum k exists | HashSet Existence Template |
| Longest subarray with sum k | Prefix Sum → First Index |
| Check zero sum subarray | Repeated Prefix Sum |
| Count zero sum subarrays | Prefix Sum Frequency |
| Longest zero sum subarray | Prefix Sum First Index |
| Equal 0s and 1s | Convert 0 to -1 |
| Sum divisible by k | Remainder Frequency |

---

## How to Decide Which Template to Use?

Ask:

```txt
What is the question asking?
```

| Question Asks | Store In Map |
|---|---|
| Count subarrays | prefix sum → frequency |
| Longest subarray | prefix sum → first index |
| Existence only | HashSet of prefix sums |
| Equal 0 and 1 | transformed prefix sum → first index |
| Divisible by k | remainder → frequency |

---

## Beginner Rule

Prefix Sum + HashMap mainly depends on this formula:

```txt
currentSum - oldPrefixSum = k
```

So:

```txt
oldPrefixSum = currentSum - k
```

In code:

```java
int need = currentSum - k;
```

For count:

```java
count += map.getOrDefault(need, 0);
```

For longest length:

```java
length = i - map.get(need);
```
