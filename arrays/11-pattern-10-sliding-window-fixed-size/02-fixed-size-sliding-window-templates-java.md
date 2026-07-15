# Fixed Size Sliding Window Templates in Java

This file contains common templates for Fixed Size Sliding Window problems.

Use these templates when the problem is about a continuous subarray or window of fixed size `k`.

---

## Template 1: Maximum Sum of Subarray of Size K

Use when question asks:

```txt
Find maximum sum among all subarrays of size k.
```

Code:

```java
public int maxSumSubarraySizeK(int[] nums, int k) {
    int windowSum = 0;

    for (int i = 0; i < k; i++) {
        windowSum += nums[i];
    }

    int maxSum = windowSum;

    for (int i = k; i < nums.length; i++) {
        windowSum = windowSum - nums[i - k] + nums[i];

        if (windowSum > maxSum) {
            maxSum = windowSum;
        }
    }

    return maxSum;
}
```

---

## Template 2: Minimum Sum of Subarray of Size K

Use when question asks:

```txt
Find minimum sum among all subarrays of size k.
```

Code:

```java
public int minSumSubarraySizeK(int[] nums, int k) {
    int windowSum = 0;

    for (int i = 0; i < k; i++) {
        windowSum += nums[i];
    }

    int minSum = windowSum;

    for (int i = k; i < nums.length; i++) {
        windowSum = windowSum - nums[i - k] + nums[i];

        if (windowSum < minSum) {
            minSum = windowSum;
        }
    }

    return minSum;
}
```

---

## Template 3: Maximum Average Subarray

Use when question asks:

```txt
Find maximum average of subarray of size k.
```

Code:

```java
public double findMaxAverage(int[] nums, int k) {
    int windowSum = 0;

    for (int i = 0; i < k; i++) {
        windowSum += nums[i];
    }

    int maxSum = windowSum;

    for (int i = k; i < nums.length; i++) {
        windowSum = windowSum - nums[i - k] + nums[i];

        if (windowSum > maxSum) {
            maxSum = windowSum;
        }
    }

    return (double) maxSum / k;
}
```

---

## Template 4: Count Windows With Sum Greater Than X

Use when question asks:

```txt
Count subarrays of size k whose sum is greater than x.
```

Code:

```java
public int countWindowsGreaterThanX(int[] nums, int k, int x) {
    int windowSum = 0;

    for (int i = 0; i < k; i++) {
        windowSum += nums[i];
    }

    int count = 0;

    if (windowSum > x) {
        count++;
    }

    for (int i = k; i < nums.length; i++) {
        windowSum = windowSum - nums[i - k] + nums[i];

        if (windowSum > x) {
            count++;
        }
    }

    return count;
}
```

---

## Template 5: Count Windows With Exact Sum X

Use when question asks:

```txt
Count subarrays of size k whose sum is exactly x.
```

Code:

```java
public int countWindowsWithSumX(int[] nums, int k, int x) {
    int windowSum = 0;

    for (int i = 0; i < k; i++) {
        windowSum += nums[i];
    }

    int count = 0;

    if (windowSum == x) {
        count++;
    }

    for (int i = k; i < nums.length; i++) {
        windowSum = windowSum - nums[i - k] + nums[i];

        if (windowSum == x) {
            count++;
        }
    }

    return count;
}
```

---

## Template 6: Print All Window Sums

Use when question asks:

```txt
Print sum of every subarray of size k.
```

Code:

```java
public void printWindowSums(int[] nums, int k) {
    int windowSum = 0;

    for (int i = 0; i < k; i++) {
        windowSum += nums[i];
    }

    System.out.println(windowSum);

    for (int i = k; i < nums.length; i++) {
        windowSum = windowSum - nums[i - k] + nums[i];
        System.out.println(windowSum);
    }
}
```

---

## Template 7: First Negative Number in Every Window

Use when question asks:

```txt
Find first negative number in each window of size k.
```

Code:

```java
import java.util.LinkedList;
import java.util.Queue;

public int[] firstNegativeInWindow(int[] nums, int k) {
    Queue<Integer> queue = new LinkedList<>();
    int[] result = new int[nums.length - k + 1];

    int index = 0;

    for (int i = 0; i < nums.length; i++) {
        if (nums[i] < 0) {
            queue.add(i);
        }

        if (!queue.isEmpty() && queue.peek() <= i - k) {
            queue.remove();
        }

        if (i >= k - 1) {
            if (!queue.isEmpty()) {
                result[index] = nums[queue.peek()];
            }
            else {
                result[index] = 0;
            }

            index++;
        }
    }

    return result;
}
```

---

## Template 8: Generic Fixed Window Template

Use this when you understand what should happen inside every window.

```java
public void fixedWindow(int[] nums, int k) {
    int windowValue = 0;

    for (int i = 0; i < k; i++) {
        windowValue += nums[i];
    }

    // process first window here

    for (int i = k; i < nums.length; i++) {
        windowValue = windowValue - nums[i - k] + nums[i];

        // process current window here
    }
}
```

---

## Template Selection Table

| Requirement | Template |
|---|---|
| Maximum sum of size k | Max Sum Template |
| Minimum sum of size k | Min Sum Template |
| Maximum average | Max Average Template |
| Count sum greater than x | Count Greater Than X |
| Count exact sum x | Count Exact Sum X |
| Print all window sums | Print Window Sums |
| First negative in window | Queue + Sliding Window |
| General fixed window problem | Generic Fixed Window |

---

## How to Decide Which Template to Use?

Ask:

```txt
What do I need from every window?
```

| Need | Track |
|---|---|
| Maximum sum | `maxSum` |
| Minimum sum | `minSum` |
| Average | `maxSum / k` |
| Count windows | `count` |
| First negative | queue of indexes |
| Every window sum | print/store `windowSum` |

---

## Beginner Rule

Fixed Size Sliding Window has one main formula:

```txt
new window = old window - outgoing element + incoming element
```

In code:

```java
windowSum = windowSum - nums[i - k] + nums[i];
```

Remember:

```txt
nums[i]     → new element entering
nums[i - k] → old element leaving
```
