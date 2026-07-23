# Day 21 Easy Mixed Java Solutions

This file contains Java solutions for Day 21 easy mixed array practice.

Focus on pattern identification before reading the solution.

---

## 1. Find Maximum Element

```java
public int findMax(int[] nums) {
    int max = nums[0];

    for (int i = 1; i < nums.length; i++) {
        if (nums[i] > max) {
            max = nums[i];
        }
    }

    return max;
}
```

Pattern:

```txt
Traversal
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

## 2. Linear Search

```java
public int linearSearch(int[] nums, int target) {
    for (int i = 0; i < nums.length; i++) {
        if (nums[i] == target) {
            return i;
        }
    }

    return -1;
}
```

Pattern:

```txt
Linear Search
```

---

## 3. Binary Search

```java
public int binarySearch(int[] nums, int target) {
    int left = 0;
    int right = nums.length - 1;

    while (left <= right) {
        int mid = left + (right - left) / 2;

        if (nums[mid] == target) {
            return mid;
        }
        else if (nums[mid] < target) {
            left = mid + 1;
        }
        else {
            right = mid - 1;
        }
    }

    return -1;
}
```

Pattern:

```txt
Binary Search
```

---

## 4. Contains Duplicate

```java
import java.util.HashSet;

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

Pattern:

```txt
HashSet
```

---

## 5. Count Frequency of Target

```java
public int countTarget(int[] nums, int target) {
    int count = 0;

    for (int i = 0; i < nums.length; i++) {
        if (nums[i] == target) {
            count++;
        }
    }

    return count;
}
```

Pattern:

```txt
Traversal
```

---

## 6. Frequency of All Elements

```java
import java.util.HashMap;

public HashMap<Integer, Integer> frequencyMap(int[] nums) {
    HashMap<Integer, Integer> map = new HashMap<>();

    for (int i = 0; i < nums.length; i++) {
        map.put(nums[i], map.getOrDefault(nums[i], 0) + 1);
    }

    return map;
}
```

Pattern:

```txt
HashMap Frequency
```

---

## 7. Remove Element

```java
public int removeElement(int[] nums, int val) {
    int index = 0;

    for (int i = 0; i < nums.length; i++) {
        if (nums[i] != val) {
            nums[index] = nums[i];
            index++;
        }
    }

    return index;
}
```

Pattern:

```txt
In-place Overwrite
```

---

## 8. Move Zeroes

```java
public void moveZeroes(int[] nums) {
    int index = 0;

    for (int i = 0; i < nums.length; i++) {
        if (nums[i] != 0) {
            nums[index] = nums[i];
            index++;
        }
    }

    while (index < nums.length) {
        nums[index] = 0;
        index++;
    }
}
```

Pattern:

```txt
In-place Overwrite
```

---

## 9. Two Sum in Sorted Array

```java
public int[] twoSumSorted(int[] nums, int target) {
    int left = 0;
    int right = nums.length - 1;

    while (left < right) {
        int sum = nums[left] + nums[right];

        if (sum == target) {
            return new int[]{left, right};
        }
        else if (sum < target) {
            left++;
        }
        else {
            right--;
        }
    }

    return new int[]{-1, -1};
}
```

Pattern:

```txt
Two Pointers
```

---

## 10. Reverse Array

```java
public void reverseArray(int[] nums) {
    int left = 0;
    int right = nums.length - 1;

    while (left < right) {
        int temp = nums[left];
        nums[left] = nums[right];
        nums[right] = temp;

        left++;
        right--;
    }
}
```

Pattern:

```txt
Two Pointers
```

---

## 11. Maximum Sum of Subarray Size K

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

Pattern:

```txt
Fixed Size Sliding Window
```

---

## 12. Longest Subarray Sum At Most K

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

Pattern:

```txt
Variable Size Sliding Window
```

Important:

```txt
This works safely when values are non-negative.
```

---

## 13. Running Sum

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

Pattern:

```txt
Prefix Sum
```

---

## 14. Range Sum Query

```java
public int rangeSum(int[] nums, int left, int right) {
    int[] prefix = new int[nums.length + 1];

    for (int i = 0; i < nums.length; i++) {
        prefix[i + 1] = prefix[i] + nums[i];
    }

    return prefix[right + 1] - prefix[left];
}
```

Pattern:

```txt
Prefix Sum
```

---

## 15. Count Subarrays With Sum K

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

Pattern:

```txt
Prefix Sum + HashMap
```

---

## 16. Maximum Subarray Sum

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

Pattern:

```txt
Kadane's Algorithm
```

---

## 17. Best Time to Buy and Sell Stock

```java
public int maxProfit(int[] prices) {
    int minPrice = prices[0];
    int maxProfit = 0;

    for (int i = 1; i < prices.length; i++) {
        if (prices[i] < minPrice) {
            minPrice = prices[i];
        }
        else {
            int profit = prices[i] - minPrice;

            if (profit > maxProfit) {
                maxProfit = profit;
            }
        }
    }

    return maxProfit;
}
```

Pattern:

```txt
Stock Profit
```

---

## 18. Single Number

```java
public int singleNumber(int[] nums) {
    int xor = 0;

    for (int i = 0; i < nums.length; i++) {
        xor = xor ^ nums[i];
    }

    return xor;
}
```

Pattern:

```txt
XOR
```

---

## 19. Missing Number

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

Pattern:

```txt
Math Formula
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

## 20. Matrix Sum

```java
public int matrixSum(int[][] matrix) {
    int rows = matrix.length;
    int cols = matrix[0].length;

    int sum = 0;

    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            sum += matrix[i][j];
        }
    }

    return sum;
}
```

Pattern:

```txt
Matrix Traversal
```

---

# Final Note

Do not memorize these solutions only.

For each solution, remember:

```txt
Problem signal → Pattern → Logic → Code
```
