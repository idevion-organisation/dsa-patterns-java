# Day 22 Medium Mixed Java Solutions

This file contains Java solutions for Day 22 medium mixed array practice.

Before reading the solution, identify:

```txt
Problem signal → Pattern → Why pattern fits
```

---

## 1. Search Insert Position

```java
public int searchInsert(int[] nums, int target) {
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

    return left;
}
```

Pattern:

```txt
Binary Search
```

Time:

```txt
O(log n)
```

Space:

```txt
O(1)
```

---

## 2. First and Last Position of Element

```java
public int[] searchRange(int[] nums, int target) {
    int first = findFirst(nums, target);
    int last = findLast(nums, target);

    return new int[]{first, last};
}

private int findFirst(int[] nums, int target) {
    int left = 0;
    int right = nums.length - 1;
    int answer = -1;

    while (left <= right) {
        int mid = left + (right - left) / 2;

        if (nums[mid] == target) {
            answer = mid;
            right = mid - 1;
        }
        else if (nums[mid] < target) {
            left = mid + 1;
        }
        else {
            right = mid - 1;
        }
    }

    return answer;
}

private int findLast(int[] nums, int target) {
    int left = 0;
    int right = nums.length - 1;
    int answer = -1;

    while (left <= right) {
        int mid = left + (right - left) / 2;

        if (nums[mid] == target) {
            answer = mid;
            left = mid + 1;
        }
        else if (nums[mid] < target) {
            left = mid + 1;
        }
        else {
            right = mid - 1;
        }
    }

    return answer;
}
```

Pattern:

```txt
Binary Search Variation
```

---

## 3. Merge Sorted Array

```java
public void merge(int[] nums1, int m, int[] nums2, int n) {
    int i = m - 1;
    int j = n - 1;
    int k = m + n - 1;

    while (i >= 0 && j >= 0) {
        if (nums1[i] > nums2[j]) {
            nums1[k] = nums1[i];
            i--;
        }
        else {
            nums1[k] = nums2[j];
            j--;
        }

        k--;
    }

    while (j >= 0) {
        nums1[k] = nums2[j];
        j--;
        k--;
    }
}
```

Pattern:

```txt
Merge Sorted Arrays
```

Important:

```txt
Merge from end to avoid overwriting valid nums1 values.
```

---

## 4. 3Sum

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

public List<List<Integer>> threeSum(int[] nums) {
    Arrays.sort(nums);

    List<List<Integer>> answer = new ArrayList<>();

    for (int i = 0; i < nums.length - 2; i++) {
        if (i > 0 && nums[i] == nums[i - 1]) {
            continue;
        }

        int left = i + 1;
        int right = nums.length - 1;

        while (left < right) {
            int sum = nums[i] + nums[left] + nums[right];

            if (sum == 0) {
                List<Integer> triplet = new ArrayList<>();
                triplet.add(nums[i]);
                triplet.add(nums[left]);
                triplet.add(nums[right]);
                answer.add(triplet);

                left++;
                right--;

                while (left < right && nums[left] == nums[left - 1]) {
                    left++;
                }

                while (left < right && nums[right] == nums[right + 1]) {
                    right--;
                }
            }
            else if (sum < 0) {
                left++;
            }
            else {
                right--;
            }
        }
    }

    return answer;
}
```

Pattern:

```txt
Sorting + Two Pointers
```

Time:

```txt
O(n²)
```

Space:

```txt
O(1) extra excluding answer
```

---

## 5. Maximum Product of Two Elements

```java
public int maxProduct(int[] nums) {
    int largest = 0;
    int secondLargest = 0;

    for (int i = 0; i < nums.length; i++) {
        if (nums[i] > largest) {
            secondLargest = largest;
            largest = nums[i];
        }
        else if (nums[i] > secondLargest) {
            secondLargest = nums[i];
        }
    }

    return (largest - 1) * (secondLargest - 1);
}
```

Pattern:

```txt
Traversal
```

---

## 6. Longest Consecutive Sequence

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

Pattern:

```txt
HashSet
```

Important:

```txt
Start counting only when num - 1 does not exist.
```

---

## 7. Subarray Product Less Than K

```java
public int numSubarrayProductLessThanK(int[] nums, int k) {
    if (k <= 1) {
        return 0;
    }

    int left = 0;
    int count = 0;
    int product = 1;

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

Pattern:

```txt
Variable Size Sliding Window
```

---

## 8. Minimum Size Subarray Sum

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

Pattern:

```txt
Variable Size Sliding Window
```

---

## 9. Max Consecutive Ones III

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

Pattern:

```txt
Variable Size Sliding Window
```

---

## 10. Product of Array Except Self

```java
public int[] productExceptSelf(int[] nums) {
    int n = nums.length;
    int[] answer = new int[n];

    int prefix = 1;

    for (int i = 0; i < n; i++) {
        answer[i] = prefix;
        prefix = prefix * nums[i];
    }

    int suffix = 1;

    for (int i = n - 1; i >= 0; i--) {
        answer[i] = answer[i] * suffix;
        suffix = suffix * nums[i];
    }

    return answer;
}
```

Pattern:

```txt
Prefix Product + Suffix Product
```

---

## 11. Sort Colors

```java
public void sortColors(int[] nums) {
    int low = 0;
    int mid = 0;
    int high = nums.length - 1;

    while (mid <= high) {
        if (nums[mid] == 0) {
            swap(nums, low, mid);
            low++;
            mid++;
        }
        else if (nums[mid] == 1) {
            mid++;
        }
        else {
            swap(nums, mid, high);
            high--;
        }
    }
}

private void swap(int[] nums, int i, int j) {
    int temp = nums[i];
    nums[i] = nums[j];
    nums[j] = temp;
}
```

Pattern:

```txt
Dutch National Flag
```

---

## 12. Rotate Array

```java
public void rotate(int[] nums, int k) {
    int n = nums.length;

    k = k % n;

    reverse(nums, 0, n - 1);
    reverse(nums, 0, k - 1);
    reverse(nums, k, n - 1);
}

private void reverse(int[] nums, int left, int right) {
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
Rotate Array using Reverse
```

---

## 13. Subarray Sum Equals K

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

## 14. Maximum Subarray Sum

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

## 15. Corporate Flight Bookings

```java
public int[] corpFlightBookings(int[][] bookings, int n) {
    int[] diff = new int[n];

    for (int i = 0; i < bookings.length; i++) {
        int left = bookings[i][0] - 1;
        int right = bookings[i][1] - 1;
        int seats = bookings[i][2];

        diff[left] += seats;

        if (right + 1 < n) {
            diff[right + 1] -= seats;
        }
    }

    int[] answer = new int[n];
    answer[0] = diff[0];

    for (int i = 1; i < n; i++) {
        answer[i] = answer[i - 1] + diff[i];
    }

    return answer;
}
```

Pattern:

```txt
Difference Array
```

Important:

```txt
Bookings are usually 1-indexed, so convert to 0-indexed.
```

---

## 16. Spiral Matrix

```java
import java.util.ArrayList;
import java.util.List;

public List<Integer> spiralOrder(int[][] matrix) {
    List<Integer> answer = new ArrayList<>();

    int top = 0;
    int bottom = matrix.length - 1;
    int left = 0;
    int right = matrix[0].length - 1;

    while (top <= bottom && left <= right) {
        for (int j = left; j <= right; j++) {
            answer.add(matrix[top][j]);
        }
        top++;

        for (int i = top; i <= bottom; i++) {
            answer.add(matrix[i][right]);
        }
        right--;

        if (top <= bottom) {
            for (int j = right; j >= left; j--) {
                answer.add(matrix[bottom][j]);
            }
            bottom--;
        }

        if (left <= right) {
            for (int i = bottom; i >= top; i--) {
                answer.add(matrix[i][left]);
            }
            left++;
        }
    }

    return answer;
}
```

Pattern:

```txt
Matrix Boundary Traversal
```

---

## 17. Set Matrix Zeroes

Beginner-friendly version using extra arrays:

```java
public void setZeroes(int[][] matrix) {
    int rows = matrix.length;
    int cols = matrix[0].length;

    boolean[] zeroRows = new boolean[rows];
    boolean[] zeroCols = new boolean[cols];

    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            if (matrix[i][j] == 0) {
                zeroRows[i] = true;
                zeroCols[j] = true;
            }
        }
    }

    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            if (zeroRows[i] || zeroCols[j]) {
                matrix[i][j] = 0;
            }
        }
    }
}
```

Pattern:

```txt
Matrix Marking
```

Time:

```txt
O(rows × cols)
```

Space:

```txt
O(rows + cols)
```

---

## 18. Find Pivot Index

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

Pattern:

```txt
Prefix / Total Sum
```

---

## 19. Set Mismatch

```java
public int[] findErrorNums(int[] nums) {
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

Pattern:

```txt
Frequency Array
```

---

## 20. Best Time to Buy and Sell Stock II

```java
public int maxProfit(int[] prices) {
    int profit = 0;

    for (int i = 1; i < prices.length; i++) {
        if (prices[i] > prices[i - 1]) {
            profit += prices[i] - prices[i - 1];
        }
    }

    return profit;
}
```

Pattern:

```txt
Stock Profit Multiple Transactions
```

---

# Final Day 22 Solution Summary

| Problem | Time | Space |
|---|---:|---:|
| Search Insert | O(log n) | O(1) |
| First and Last Position | O(log n) | O(1) |
| Merge Sorted Array | O(m + n) | O(1) |
| 3Sum | O(n²) | O(1) extra |
| Maximum Product Two Elements | O(n) | O(1) |
| Longest Consecutive | O(n) average | O(n) |
| Subarray Product Less Than K | O(n) | O(1) |
| Minimum Size Subarray Sum | O(n) | O(1) |
| Max Consecutive Ones III | O(n) | O(1) |
| Product Except Self | O(n) | O(1) extra |
| Sort Colors | O(n) | O(1) |
| Rotate Array | O(n) | O(1) |
| Subarray Sum Equals K | O(n) average | O(n) |
| Maximum Subarray | O(n) | O(1) |
| Corporate Flight Bookings | O(n + q) | O(n) |
| Spiral Matrix | O(rows × cols) | O(rows × cols) |
| Set Matrix Zeroes | O(rows × cols) | O(rows + cols) |
| Pivot Index | O(n) | O(1) |
| Set Mismatch | O(n) | O(n) |
| Stock II | O(n) | O(1) |
