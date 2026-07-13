# Sorting-Based Templates in Java

This file contains common templates for Sorting-Based array problems.

Use these templates when sorting gives structure to the problem.

---

## Required Import

```java
import java.util.Arrays;
```

---

## Template 1: Sort Array

Use when question asks:

```txt
Sort the array in ascending order.
```

Code:

```java
public void sortArray(int[] nums) {
    Arrays.sort(nums);
}
```

---

## Template 2: Contains Duplicate Using Sorting

Use when question asks:

```txt
Check if duplicate exists.
```

Code:

```java
public boolean containsDuplicate(int[] nums) {
    Arrays.sort(nums);

    for (int i = 1; i < nums.length; i++) {
        if (nums[i] == nums[i - 1]) {
            return true;
        }
    }

    return false;
}
```

---

## Template 3: Count Unique Elements

Use when question asks:

```txt
Count distinct elements.
```

Code:

```java
public int countUnique(int[] nums) {
    if (nums.length == 0) {
        return 0;
    }

    Arrays.sort(nums);

    int count = 1;

    for (int i = 1; i < nums.length; i++) {
        if (nums[i] != nums[i - 1]) {
            count++;
        }
    }

    return count;
}
```

---

## Template 4: Kth Smallest Element

Use when question asks:

```txt
Find kth smallest element.
```

Code:

```java
public int kthSmallest(int[] nums, int k) {
    Arrays.sort(nums);

    return nums[k - 1];
}
```

Formula:

```txt
kth smallest = nums[k - 1]
```

---

## Template 5: Kth Largest Element

Use when question asks:

```txt
Find kth largest element.
```

Code:

```java
public int kthLargest(int[] nums, int k) {
    Arrays.sort(nums);

    return nums[nums.length - k];
}
```

Formula:

```txt
kth largest = nums[n - k]
```

---

## Template 6: Minimum Difference

Use when question asks:

```txt
Find minimum difference between any two elements.
```

Code:

```java
public int minimumDifference(int[] nums) {
    Arrays.sort(nums);

    int minDiff = Integer.MAX_VALUE;

    for (int i = 1; i < nums.length; i++) {
        int diff = nums[i] - nums[i - 1];

        if (diff < minDiff) {
            minDiff = diff;
        }
    }

    return minDiff;
}
```

Important:

```txt
After sorting, minimum difference will be between adjacent elements.
```

---

## Template 7: Pair Sum After Sorting

Use when question asks:

```txt
Check if any pair has target sum.
Original indexes are not required.
```

Code:

```java
public boolean hasPairSum(int[] nums, int target) {
    Arrays.sort(nums);

    int left = 0;
    int right = nums.length - 1;

    while (left < right) {
        int sum = nums[left] + nums[right];

        if (sum == target) {
            return true;
        }
        else if (sum < target) {
            left++;
        }
        else {
            right--;
        }
    }

    return false;
}
```

---

## Template 8: Longest Consecutive Sequence Using Sorting

Use when question asks:

```txt
Find longest consecutive sequence.
```

Code:

```java
public int longestConsecutive(int[] nums) {
    if (nums.length == 0) {
        return 0;
    }

    Arrays.sort(nums);

    int longest = 1;
    int current = 1;

    for (int i = 1; i < nums.length; i++) {
        if (nums[i] == nums[i - 1]) {
            continue;
        }
        else if (nums[i] == nums[i - 1] + 1) {
            current++;
        }
        else {
            current = 1;
        }

        if (current > longest) {
            longest = current;
        }
    }

    return longest;
}
```

---

## Template 9: Sort 0s, 1s, and 2s

Use when question asks:

```txt
Sort an array containing only 0, 1, and 2.
```

Beginner sorting solution:

```java
public void sortColors(int[] nums) {
    Arrays.sort(nums);
}
```

Optimized pattern:

```txt
Dutch National Flag
```

will be covered later.

---

## Template 10: Third Maximum Distinct Number

Use when question asks:

```txt
Return third distinct maximum number.
If third maximum does not exist, return maximum.
```

Code:

```java
public int thirdMax(int[] nums) {
    Arrays.sort(nums);

    int distinctCount = 1;
    int max = nums[nums.length - 1];

    for (int i = nums.length - 2; i >= 0; i--) {
        if (nums[i] != nums[i + 1]) {
            distinctCount++;

            if (distinctCount == 3) {
                return nums[i];
            }
        }
    }

    return max;
}
```

Why reverse loop?

```txt
After sorting, largest elements are at the end.
```

---

## Template Selection Table

| Requirement | Template |
|---|---|
| Sort array | Sort Array |
| Check duplicate | Contains Duplicate |
| Count unique values | Count Unique |
| Kth smallest | Kth Smallest |
| Kth largest | Kth Largest |
| Minimum difference | Minimum Difference |
| Pair sum values | Sorting + Two Pointers |
| Longest consecutive sequence | Sort + Scan |
| Sort 0,1,2 | Basic Sort / Dutch Flag later |
| Third distinct maximum | Sort + Reverse Scan |

---

## How to Decide Which Template to Use?

Ask:

```txt
What does sorting help me see?
```

| After Sorting | Useful For |
|---|---|
| Duplicates become adjacent | duplicate check, unique count |
| Smallest values come first | kth smallest |
| Largest values go last | kth largest |
| Closest values become nearby | min difference |
| Sorted order allows pointer movement | pair sum |
| Consecutive values become adjacent | longest consecutive |

---

## Beginner Rule

Sorting is useful when:

```txt
The problem becomes easier after arranging values.
```

But always check:

```txt
Can I change the order?
Does original index matter?
Is O(n log n) acceptable?
```
