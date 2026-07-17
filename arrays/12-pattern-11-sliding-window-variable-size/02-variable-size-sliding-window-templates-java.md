# Variable Size Sliding Window Templates in Java

This file contains common templates for Variable Size Sliding Window problems.

Use these templates when the window size changes based on a condition.

---

## Template 1: Longest Subarray With Sum At Most K

Use when question asks:

```txt
Find longest subarray whose sum is <= k.
Array contains positive or non-negative numbers.
```

Code:

```java
public int longestSubarraySumAtMostK(int[] nums, int k) {
    int left = 0;
    int windowSum = 0;
    int maxLength = 0;

    for (int right = 0; right < nums.length; right++) {
        windowSum += nums[right];

        while (windowSum > k) {
            windowSum -= nums[left];
            left++;
        }

        int length = right - left + 1;

        if (length > maxLength) {
            maxLength = length;
        }
    }

    return maxLength;
}
```

---

## Template 2: Minimum Size Subarray Sum

Use when question asks:

```txt
Find minimum length subarray whose sum is >= target.
Array contains positive numbers.
```

Code:

```java
public int minSubArrayLen(int target, int[] nums) {
    int left = 0;
    int windowSum = 0;
    int minLength = Integer.MAX_VALUE;

    for (int right = 0; right < nums.length; right++) {
        windowSum += nums[right];

        while (windowSum >= target) {
            int length = right - left + 1;

            if (length < minLength) {
                minLength = length;
            }

            windowSum -= nums[left];
            left++;
        }
    }

    if (minLength == Integer.MAX_VALUE) {
        return 0;
    }

    return minLength;
}
```

---

## Template 3: Count Subarrays With Sum At Most K

Use when question asks:

```txt
Count subarrays whose sum is <= k.
Array contains non-negative numbers.
```

Code:

```java
public int countSubarraysSumAtMostK(int[] nums, int k) {
    int left = 0;
    int windowSum = 0;
    int count = 0;

    for (int right = 0; right < nums.length; right++) {
        windowSum += nums[right];

        while (windowSum > k) {
            windowSum -= nums[left];
            left++;
        }

        count += right - left + 1;
    }

    return count;
}
```

Why:

```txt
After shrinking, every subarray ending at right and starting from left to right is valid.
```

---

## Template 4: Longest Subarray With At Most K Zeroes

Use when question asks:

```txt
Find longest subarray with at most k zeroes.
```

Code:

```java
public int longestOnes(int[] nums, int k) {
    int left = 0;
    int zeroCount = 0;
    int maxLength = 0;

    for (int right = 0; right < nums.length; right++) {
        if (nums[right] == 0) {
            zeroCount++;
        }

        while (zeroCount > k) {
            if (nums[left] == 0) {
                zeroCount--;
            }

            left++;
        }

        int length = right - left + 1;

        if (length > maxLength) {
            maxLength = length;
        }
    }

    return maxLength;
}
```

---

## Template 5: Count Subarrays With Product Less Than K

Use when question asks:

```txt
Count subarrays whose product is less than k.
Array contains positive numbers.
```

Code:

```java
public int numSubarrayProductLessThanK(int[] nums, int k) {
    if (k <= 1) {
        return 0;
    }

    int left = 0;
    long product = 1;
    int count = 0;

    for (int right = 0; right < nums.length; right++) {
        product *= nums[right];

        while (product >= k) {
            product /= nums[left];
            left++;
        }

        count += right - left + 1;
    }

    return count;
}
```

---

## Template 6: Longest Subarray With At Most K Distinct Values

Use when question asks:

```txt
Find longest subarray with at most k distinct values.
```

This uses HashMap with Sliding Window.

Code:

```java
import java.util.HashMap;

public int longestSubarrayAtMostKDistinct(int[] nums, int k) {
    HashMap<Integer, Integer> map = new HashMap<>();

    int left = 0;
    int maxLength = 0;

    for (int right = 0; right < nums.length; right++) {
        map.put(nums[right], map.getOrDefault(nums[right], 0) + 1);

        while (map.size() > k) {
            map.put(nums[left], map.get(nums[left]) - 1);

            if (map.get(nums[left]) == 0) {
                map.remove(nums[left]);
            }

            left++;
        }

        int length = right - left + 1;

        if (length > maxLength) {
            maxLength = length;
        }
    }

    return maxLength;
}
```

---

## Template 7: Generic Variable Window Template

Use this when window size changes based on condition.

```java
public void variableWindow(int[] nums) {
    int left = 0;

    for (int right = 0; right < nums.length; right++) {
        // add nums[right] to window

        while (window is invalid) {
            // remove nums[left] from window
            left++;
        }

        // update answer when window is valid
    }
}
```

---

## Template Selection Table

| Requirement | Template |
|---|---|
| Longest sum <= k | Longest Subarray Sum At Most K |
| Minimum sum >= target | Minimum Size Subarray Sum |
| Count sum <= k | Count Subarrays Sum At Most K |
| At most k zeroes | Longest Ones |
| Product less than k | Product Window |
| At most k distinct | HashMap + Sliding Window |
| General condition window | Generic Variable Window |

---

## How to Decide Which Template to Use?

Ask:

```txt
What makes my window invalid?
```

| Problem | Invalid Condition |
|---|---|
| Sum at most k | `windowSum > k` |
| Sum at least target minimum length | valid while `windowSum >= target` |
| At most k zeroes | `zeroCount > k` |
| Product less than k | `product >= k` |
| At most k distinct | `map.size() > k` |

---

## Beginner Rule

Variable Size Sliding Window has two main actions:

```txt
Expand with right
Shrink with left
```

Remember:

```txt
right adds new elements
left removes old elements
```

The most important question is:

```txt
When is my window invalid?
```
