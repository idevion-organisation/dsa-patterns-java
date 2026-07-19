# Kadane's Algorithm Templates in Java

This file contains common Kadane's Algorithm templates.

Use these templates when the problem asks for maximum subarray sum, minimum subarray sum, or best continuous subarray value.

---

## Template 1: Maximum Subarray Sum

Use when question asks:

```txt
Find maximum sum of a continuous subarray.
```

Code:

```java
public int maxSubArray(int[] nums) {
    int currentSum = nums[0];
    int maxSum = nums[0];

    for (int i = 1; i < nums.length; i++) {
        currentSum = Math.max(nums[i], currentSum + nums[i]);
        maxSum = Math.max(maxSum, currentSum);
    }

    return maxSum;
}
```

Time:

```txt
O(n)
```

Space:

```txt
O(1)
```

---

## Template 2: Maximum Subarray Sum Beginner Version

Use when you prefer the reset-style approach.

Code:

```java
public int maxSubArray(int[] nums) {
    int maxSum = nums[0];
    int currentSum = 0;

    for (int i = 0; i < nums.length; i++) {
        currentSum += nums[i];

        if (currentSum > maxSum) {
            maxSum = currentSum;
        }

        if (currentSum < 0) {
            currentSum = 0;
        }
    }

    return maxSum;
}
```

Important:

```txt
maxSum should be initialized with nums[0].
```

---

## Template 3: Maximum Subarray Sum With Indexes

Use when question asks:

```txt
Return maximum sum along with start and end index.
```

Code:

```java
public int[] maxSubArrayWithIndexes(int[] nums) {
    int currentSum = nums[0];
    int maxSum = nums[0];

    int start = 0;
    int end = 0;
    int tempStart = 0;

    for (int i = 1; i < nums.length; i++) {
        if (nums[i] > currentSum + nums[i]) {
            currentSum = nums[i];
            tempStart = i;
        }
        else {
            currentSum = currentSum + nums[i];
        }

        if (currentSum > maxSum) {
            maxSum = currentSum;
            start = tempStart;
            end = i;
        }
    }

    return new int[]{maxSum, start, end};
}
```

Return:

```txt
[maxSum, startIndex, endIndex]
```

---

## Template 4: Minimum Subarray Sum

Use when question asks:

```txt
Find minimum sum of a continuous subarray.
```

Code:

```java
public int minSubArray(int[] nums) {
    int currentSum = nums[0];
    int minSum = nums[0];

    for (int i = 1; i < nums.length; i++) {
        currentSum = Math.min(nums[i], currentSum + nums[i]);
        minSum = Math.min(minSum, currentSum);
    }

    return minSum;
}
```

---

## Template 5: Maximum Absolute Subarray Sum

Use when question asks:

```txt
Find maximum absolute sum of any subarray.
```

Code:

```java
public int maxAbsoluteSum(int[] nums) {
    int maxCurrent = nums[0];
    int maxSum = nums[0];

    int minCurrent = nums[0];
    int minSum = nums[0];

    for (int i = 1; i < nums.length; i++) {
        maxCurrent = Math.max(nums[i], maxCurrent + nums[i]);
        maxSum = Math.max(maxSum, maxCurrent);

        minCurrent = Math.min(nums[i], minCurrent + nums[i]);
        minSum = Math.min(minSum, minCurrent);
    }

    return Math.max(Math.abs(maxSum), Math.abs(minSum));
}
```

---

## Template 6: Maximum Circular Subarray Sum

Use when question asks:

```txt
Find maximum subarray sum in a circular array.
```

Example:

```txt
nums = [5, -3, 5]
```

Normal maximum subarray:

```txt
[5]
or
[5]
```

Circular maximum subarray:

```txt
[5, 5]
```

Answer:

```txt
10
```

Code:

```java
public int maxSubarraySumCircular(int[] nums) {
    int totalSum = nums[0];

    int maxCurrent = nums[0];
    int maxSum = nums[0];

    int minCurrent = nums[0];
    int minSum = nums[0];

    for (int i = 1; i < nums.length; i++) {
        totalSum += nums[i];

        maxCurrent = Math.max(nums[i], maxCurrent + nums[i]);
        maxSum = Math.max(maxSum, maxCurrent);

        minCurrent = Math.min(nums[i], minCurrent + nums[i]);
        minSum = Math.min(minSum, minCurrent);
    }

    if (maxSum < 0) {
        return maxSum;
    }

    return Math.max(maxSum, totalSum - minSum);
}
```

Logic:

```txt
Circular max = total sum - minimum subarray sum
```

Special case:

```txt
If all numbers are negative, return maxSum.
```

---

## Template 7: Check If Positive Sum Subarray Exists

Use when question asks:

```txt
Check if any subarray has positive sum.
```

Code:

```java
public boolean hasPositiveSumSubarray(int[] nums) {
    int currentSum = nums[0];
    int maxSum = nums[0];

    for (int i = 1; i < nums.length; i++) {
        currentSum = Math.max(nums[i], currentSum + nums[i]);
        maxSum = Math.max(maxSum, currentSum);
    }

    return maxSum > 0;
}
```

---

## Template Selection Table

| Requirement | Template |
|---|---|
| Maximum subarray sum | Basic Kadane |
| Easier beginner code | Reset-style Kadane |
| Need start/end index | Kadane With Indexes |
| Minimum subarray sum | Min Kadane |
| Maximum absolute sum | Max + Min Kadane |
| Circular max subarray | Circular Kadane |
| Check positive subarray | Kadane + condition |

---

## How to Decide Which Template to Use?

Ask:

```txt
What does the question want from a continuous subarray?
```

| Question Wants | Use |
|---|---|
| Largest sum | Maximum Kadane |
| Smallest sum | Minimum Kadane |
| Largest absolute sum | Max + Min Kadane |
| Circular array max sum | Circular Kadane |
| Start and end indexes | Kadane with indexes |
| Only positive existence | Kadane + check maxSum |

---

## Beginner Rule

Kadane's Algorithm is based on one decision:

```txt
Should I continue the previous subarray,
or should I start a new subarray from current element?
```

Formula:

```java
currentSum = Math.max(nums[i], currentSum + nums[i]);
```

Answer update:

```java
maxSum = Math.max(maxSum, currentSum);
```
