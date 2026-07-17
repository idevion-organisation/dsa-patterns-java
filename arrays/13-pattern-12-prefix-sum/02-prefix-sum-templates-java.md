# Prefix Sum Templates in Java

This file contains common Prefix Sum templates for array problems.

Use these templates when the problem asks for running sum, range sum, left/right sum, or multiple sum queries.

---

## Template 1: Build Prefix Sum Array

Use when question asks:

```txt
Precompute prefix sum.
```

Code:

```java
public int[] buildPrefixSum(int[] nums) {
    int[] prefix = new int[nums.length + 1];

    for (int i = 0; i < nums.length; i++) {
        prefix[i + 1] = prefix[i] + nums[i];
    }

    return prefix;
}
```

Formula:

```txt
prefix[i + 1] = prefix[i] + nums[i]
```

---

## Template 2: Range Sum Query

Use when question asks:

```txt
Find sum from left index to right index.
```

Code:

```java
public int rangeSum(int[] nums, int left, int right) {
    int[] prefix = new int[nums.length + 1];

    for (int i = 0; i < nums.length; i++) {
        prefix[i + 1] = prefix[i] + nums[i];
    }

    return prefix[right + 1] - prefix[left];
}
```

---

## Template 3: Multiple Range Sum Queries

Use when question gives:

```txt
queries[i] = [left, right]
```

Code:

```java
public int[] rangeSumQueries(int[] nums, int[][] queries) {
    int[] prefix = new int[nums.length + 1];

    for (int i = 0; i < nums.length; i++) {
        prefix[i + 1] = prefix[i] + nums[i];
    }

    int[] answer = new int[queries.length];

    for (int i = 0; i < queries.length; i++) {
        int left = queries[i][0];
        int right = queries[i][1];

        answer[i] = prefix[right + 1] - prefix[left];
    }

    return answer;
}
```

Time:

```txt
O(n + q)
```

where `q` is number of queries.

---

## Template 4: Running Sum

Use when question asks:

```txt
Return running sum of array.
```

Code:

```java
public int[] runningSum(int[] nums) {
    int[] result = new int[nums.length];

    result[0] = nums[0];

    for (int i = 1; i < nums.length; i++) {
        result[i] = result[i - 1] + nums[i];
    }

    return result;
}
```

Example:

```txt
nums = [1, 2, 3, 4]
result = [1, 3, 6, 10]
```

---

## Template 5: Running Sum In-place

Use when question allows modifying the same array.

Code:

```java
public int[] runningSumInPlace(int[] nums) {
    for (int i = 1; i < nums.length; i++) {
        nums[i] = nums[i - 1] + nums[i];
    }

    return nums;
}
```

Space:

```txt
O(1)
```

because we modify the original array.

---

## Template 6: Pivot Index

Use when question asks:

```txt
Find index where left sum equals right sum.
```

Code:

```java
public int pivotIndex(int[] nums) {
    int totalSum = 0;

    for (int i = 0; i < nums.length; i++) {
        totalSum += nums[i];
    }

    int leftSum = 0;

    for (int i = 0; i < nums.length; i++) {
        int rightSum = totalSum - leftSum - nums[i];

        if (leftSum == rightSum) {
            return i;
        }

        leftSum += nums[i];
    }

    return -1;
}
```

Formula:

```txt
rightSum = totalSum - leftSum - nums[i]
```

---

## Template 7: Left Sum Array and Right Sum Array

Use when question asks:

```txt
Find left sum and right sum for every index.
```

Code:

```java
public int[][] leftRightSumArrays(int[] nums) {
    int n = nums.length;

    int[] leftSum = new int[n];
    int[] rightSum = new int[n];

    for (int i = 1; i < n; i++) {
        leftSum[i] = leftSum[i - 1] + nums[i - 1];
    }

    for (int i = n - 2; i >= 0; i--) {
        rightSum[i] = rightSum[i + 1] + nums[i + 1];
    }

    return new int[][]{leftSum, rightSum};
}
```

Example:

```txt
nums = [1, 7, 3, 6, 5, 6]
```

At index `3`:

```txt
leftSum[3] = 11
rightSum[3] = 11
```

---

## Template 8: Difference Between Left and Right Sum

Use when question asks:

```txt
Return absolute difference between left sum and right sum for every index.
```

Code:

```java
public int[] leftRightDifference(int[] nums) {
    int n = nums.length;
    int totalSum = 0;

    for (int i = 0; i < n; i++) {
        totalSum += nums[i];
    }

    int[] answer = new int[n];
    int leftSum = 0;

    for (int i = 0; i < n; i++) {
        int rightSum = totalSum - leftSum - nums[i];

        answer[i] = Math.abs(leftSum - rightSum);

        leftSum += nums[i];
    }

    return answer;
}
```

---

## Template 9: Prefix Sum Using Long

Use when array values or sums may be large.

Code:

```java
public long[] buildPrefixSumLong(int[] nums) {
    long[] prefix = new long[nums.length + 1];

    for (int i = 0; i < nums.length; i++) {
        prefix[i + 1] = prefix[i] + nums[i];
    }

    return prefix;
}
```

Range query:

```java
public long rangeSumLong(int[] nums, int left, int right) {
    long[] prefix = new long[nums.length + 1];

    for (int i = 0; i < nums.length; i++) {
        prefix[i + 1] = prefix[i] + nums[i];
    }

    return prefix[right + 1] - prefix[left];
}
```

---

## Template Selection Table

| Requirement | Template |
|---|---|
| Build prefix array | Build Prefix Sum |
| Single range query | Range Sum Query |
| Many range queries | Multiple Range Sum Queries |
| Running sum | Running Sum |
| Modify same array | Running Sum In-place |
| Left sum equals right sum | Pivot Index |
| Left/right sum arrays | Left Sum and Right Sum |
| Difference between left/right | Left Right Difference |
| Large sums | Prefix Sum Using Long |

---

## How to Decide Which Template to Use?

Ask:

```txt
What type of sum is needed?
```

| Question Type | Use |
|---|---|
| Sum from l to r | Prefix array |
| Many range queries | Prefix array once |
| Running total at each index | Running sum |
| Left sum equals right sum | Pivot index logic |
| Large values | long prefix sum |
| Count subarrays with sum k | Prefix Sum + HashMap later |

---

## Beginner Rule

Prefix Sum is mainly about one idea:

```txt
Store previous sums so future range sums become fast.
```

Most important formula:

```java
prefix[right + 1] - prefix[left]
```

For query:

```txt
sum from left to right
```
