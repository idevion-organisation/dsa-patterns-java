# XOR and Math Formula Templates in Java

This file contains common templates for XOR and Math Formula based array problems.

Use these templates when the question has pair cancellation, missing number, known range, or mathematical counting.

---

## Template 1: Single Number Using XOR

Use when question says:

```txt
Every element appears twice except one.
Find the single element.
```

Code:

```java
public int singleNumber(int[] nums) {
    int xor = 0;

    for (int i = 0; i < nums.length; i++) {
        xor = xor ^ nums[i];
    }

    return xor;
}
```

Short version:

```java
public int singleNumber(int[] nums) {
    int xor = 0;

    for (int num : nums) {
        xor ^= num;
    }

    return xor;
}
```

---

## Template 2: Missing Number Using Formula

Use when question says:

```txt
Array contains numbers from 0 to n.
One number is missing.
```

Code:

```java
public int missingNumber(int[] nums) {
    int n = nums.length;

    int expectedSum = n * (n + 1) / 2;
    int actualSum = 0;

    for (int i = 0; i < nums.length; i++) {
        actualSum += nums[i];
    }

    return expectedSum - actualSum;
}
```

Safer version:

```java
public int missingNumber(int[] nums) {
    int n = nums.length;

    long expectedSum = (long) n * (n + 1) / 2;
    long actualSum = 0;

    for (int i = 0; i < nums.length; i++) {
        actualSum += nums[i];
    }

    return (int) (expectedSum - actualSum);
}
```

---

## Template 3: Missing Number Using XOR

Use when question says:

```txt
Array contains numbers from 0 to n.
One number is missing.
Solve without overflow risk.
```

Code:

```java
public int missingNumber(int[] nums) {
    int xor = nums.length;

    for (int i = 0; i < nums.length; i++) {
        xor = xor ^ i;
        xor = xor ^ nums[i];
    }

    return xor;
}
```

---

## Template 4: Find Duplicate and Missing Using Frequency Array

Use when question says:

```txt
Array contains numbers from 1 to n.
One number is repeated.
One number is missing.
```

Code:

```java
public int[] findDuplicateAndMissing(int[] nums) {
    int n = nums.length;
    int[] freq = new int[n + 1];

    for (int i = 0; i < nums.length; i++) {
        freq[nums[i]]++;
    }

    int duplicate = -1;
    int missing = -1;

    for (int i = 1; i <= n; i++) {
        if (freq[i] == 2) {
            duplicate = i;
        }

        if (freq[i] == 0) {
            missing = i;
        }
    }

    return new int[]{duplicate, missing};
}
```

---

## Template 5: Count Good Pairs Using Formula

Use when question asks:

```txt
Count pairs where nums[i] == nums[j] and i < j.
```

Formula:

```txt
pairs from frequency f = f * (f - 1) / 2
```

Code:

```java
import java.util.HashMap;

public int numIdenticalPairs(int[] nums) {
    HashMap<Integer, Integer> map = new HashMap<>();

    for (int i = 0; i < nums.length; i++) {
        map.put(nums[i], map.getOrDefault(nums[i], 0) + 1);
    }

    int count = 0;

    for (int key : map.keySet()) {
        int freq = map.get(key);
        count += freq * (freq - 1) / 2;
    }

    return count;
}
```

---

## Template 6: Count Good Pairs While Traversing

Use when you want a cleaner one-pass solution.

Code:

```java
import java.util.HashMap;

public int numIdenticalPairs(int[] nums) {
    HashMap<Integer, Integer> map = new HashMap<>();

    int count = 0;

    for (int i = 0; i < nums.length; i++) {
        int freq = map.getOrDefault(nums[i], 0);

        count += freq;

        map.put(nums[i], freq + 1);
    }

    return count;
}
```

Meaning:

```txt
If current number appeared freq times before,
it can form freq new pairs.
```

---

## Template 7: Sum From 1 to n

Use when you need expected sum.

Code:

```java
public int sumOneToN(int n) {
    return n * (n + 1) / 2;
}
```

Safer version:

```java
public long sumOneToN(int n) {
    return (long) n * (n + 1) / 2;
}
```

---

## Template 8: Power of Two Using Bit Logic

Use when question asks:

```txt
Check if number is power of two.
```

Code:

```java
public boolean isPowerOfTwo(int n) {
    if (n <= 0) {
        return false;
    }

    return (n & (n - 1)) == 0;
}
```

Idea:

```txt
Power of two has only one set bit.
```

This is bit manipulation, not exactly XOR, but it belongs to the same math/bit-thinking family.

---

## Template Selection Table

| Requirement | Template |
|---|---|
| One number appears once, others twice | Single Number XOR |
| Missing number from 0 to n | Formula or XOR |
| Avoid sum overflow | Missing Number XOR |
| Duplicate and missing from 1 to n | Frequency array |
| Count equal pairs | Frequency + pair formula |
| Sum from 1 to n | Sum formula |
| Power of two | Bit check |

---

## How to Decide Which Template to Use?

Ask:

```txt
What property is given?
```

| Given Property | Use |
|---|---|
| Pairs cancel | XOR |
| Range 0 to n, one missing | Formula or XOR |
| Need count of pairs | Math formula with frequency |
| Need frequency | HashMap or frequency array |
| Need exact duplicate count | HashMap/frequency |
| Sum may overflow | Use long or XOR |

---

## Beginner Rule

For XOR problems, remember:

```txt
same numbers cancel
0 does not change value
```

For math formula problems, remember:

```txt
expected answer - actual answer
```

Most used formula:

```java
n * (n + 1) / 2
```
