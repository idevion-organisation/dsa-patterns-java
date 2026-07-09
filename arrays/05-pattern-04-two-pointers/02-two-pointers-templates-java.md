# Two Pointers Templates in Java

This file contains common Two Pointers templates in Java.

Use these templates when the problem has sorted array, pair sum, reverse, palindrome, or two-side comparison.

---

## Template 1: Pair Sum Exists in Sorted Array

Use when question asks:

```txt
Check if two numbers add up to target.
Array is sorted.
Return true or false.
```

```java
public boolean hasPairWithSum(int[] nums, int target) {
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

Time:

```txt
O(n)
```

Space:

```txt
O(1)
```

---

## Template 2: Return Pair Indexes

Use when question asks:

```txt
Return indexes of two numbers whose sum is target.
Array is sorted.
```

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

Use this when indexes are zero-based.

---

## Template 3: Return Pair Values

Use when question asks:

```txt
Return the two values whose sum is target.
```

```java
public int[] twoSumValues(int[] nums, int target) {
    int left = 0;
    int right = nums.length - 1;

    while (left < right) {
        int sum = nums[left] + nums[right];

        if (sum == target) {
            return new int[]{nums[left], nums[right]};
        }
        else if (sum < target) {
            left++;
        }
        else {
            right--;
        }
    }

    return new int[]{};
}
```

---

## Template 4: Reverse Array

Use when question asks:

```txt
Reverse the array in-place.
```

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

Time:

```txt
O(n)
```

Space:

```txt
O(1)
```

---

## Template 5: Palindrome Style Check

Use when question asks:

```txt
Check if array is same from start and end.
```

```java
public boolean isPalindromeArray(int[] nums) {
    int left = 0;
    int right = nums.length - 1;

    while (left < right) {
        if (nums[left] != nums[right]) {
            return false;
        }

        left++;
        right--;
    }

    return true;
}
```

---

## Template 6: Squares of Sorted Array

Use when question asks:

```txt
Given sorted array, return squares in sorted order.
```

```java
public int[] sortedSquares(int[] nums) {
    int n = nums.length;
    int[] ans = new int[n];

    int left = 0;
    int right = n - 1;
    int index = n - 1;

    while (left <= right) {
        int leftSquare = nums[left] * nums[left];
        int rightSquare = nums[right] * nums[right];

        if (leftSquare > rightSquare) {
            ans[index] = leftSquare;
            left++;
        }
        else {
            ans[index] = rightSquare;
            right--;
        }

        index--;
    }

    return ans;
}
```

Why `left <= right` here?

```txt
Because every element must be processed, including the last remaining middle element.
```

---

## Template 7: Closest Pair Sum

Use when question asks:

```txt
Find pair sum closest to target.
Array is sorted.
```

```java
public int closestPairSum(int[] nums, int target) {
    int left = 0;
    int right = nums.length - 1;

    int closest = nums[left] + nums[right];

    while (left < right) {
        int sum = nums[left] + nums[right];

        if (Math.abs(target - sum) < Math.abs(target - closest)) {
            closest = sum;
        }

        if (sum < target) {
            left++;
        }
        else if (sum > target) {
            right--;
        }
        else {
            return sum;
        }
    }

    return closest;
}
```

---

## Template 8: Count Pairs With Sum Less Than Target

Use when question asks:

```txt
Count pairs whose sum is less than target.
Array is sorted.
```

```java
public int countPairsLessThanTarget(int[] nums, int target) {
    int left = 0;
    int right = nums.length - 1;
    int count = 0;

    while (left < right) {
        int sum = nums[left] + nums[right];

        if (sum < target) {
            count += right - left;
            left++;
        }
        else {
            right--;
        }
    }

    return count;
}
```

Why `count += right - left`?

```txt
If nums[left] + nums[right] < target,
then nums[left] can pair with every element from left + 1 to right.
```

---

## Template Selection Table

| Requirement | Template |
|---|---|
| Pair sum exists | Pair Sum Exists |
| Return pair indexes | Return Pair Indexes |
| Return pair values | Return Pair Values |
| Reverse array | Reverse Array |
| Palindrome check | Palindrome Style Check |
| Sorted squares | Squares of Sorted Array |
| Closest pair sum | Closest Pair Sum |
| Count pairs less than target | Count Pairs Less Than Target |

---

## How to Decide Which Template to Use?

Ask:

```txt
What are my two pointers representing?
```

| Situation | Pointer Meaning |
|---|---|
| Pair sum | smallest and largest possible values |
| Reverse | elements to swap |
| Palindrome | elements to compare |
| Sorted squares | largest square from left or right |
| Closest sum | current best pair |
| Count pairs | number of valid pairs |

---

## Beginner Rule

Two Pointers is not just using two variables.

It means:

```txt
Use two indexes smartly to avoid unnecessary nested loops.
```

Main question to ask:

```txt
Which pointer should move, and why?
```
