# Pattern 08: Sorting-Based Patterns

Sorting-Based Pattern is used when arranging elements in order makes the problem easier.

Sorting helps us convert a messy array into a structured array.

After sorting, we can easily apply:

```txt
adjacent comparison
two pointers
duplicate detection
kth smallest/largest
consecutive checking
minimum difference
```

---

## What Is Sorting?

Sorting means arranging elements in a specific order.

Ascending order:

```txt
[5, 1, 3, 2, 4]
```

After sorting:

```txt
[1, 2, 3, 4, 5]
```

Descending order:

```txt
[5, 4, 3, 2, 1]
```

In Java, for integer arrays, we usually use:

```java
Arrays.sort(nums);
```

This sorts the array in ascending order.

---

## Java Import

Before using `Arrays.sort()`, write:

```java
import java.util.Arrays;
```

Example:

```java
import java.util.Arrays;

class Main {
    public static void main(String[] args) {
        int[] nums = {5, 1, 3, 2, 4};

        Arrays.sort(nums);

        System.out.println(Arrays.toString(nums));
    }
}
```

Output:

```txt
[1, 2, 3, 4, 5]
```

---

## Simple Meaning

```txt
Sort the array
Use the new order to solve the problem easily
```

Sorting gives structure to the array.

Before sorting:

```txt
[4, 1, 7, 2, 1]
```

After sorting:

```txt
[1, 1, 2, 4, 7]
```

Now duplicates are together.

So duplicate checking becomes easy.

---

## Pattern Signal

Think of Sorting-Based Pattern when the question says:

```txt
smallest
largest
minimum difference
maximum difference
kth smallest
kth largest
duplicate
unique
consecutive
pair sum
can reorder array
order does not matter
```

Most common signal:

```txt
If sorting makes similar values come together, use sorting.
```

---

## When Sorting Is Useful

Sorting is useful when:

```txt
order of elements does not matter
we only need values, not original positions
duplicates need to be grouped
we need smallest/largest/kth value
we need to compare nearby values
we need to use two pointers on an unsorted array
```

Example:

```txt
Find duplicate in array.
```

Unsorted:

```txt
[3, 1, 4, 2, 3]
```

Sorted:

```txt
[1, 2, 3, 3, 4]
```

Now duplicate `3` is adjacent.

---

## When Not to Use Sorting

Do not blindly sort every array problem.

Avoid sorting when:

```txt
original index is important
relative order must be maintained
question asks for in-place without changing order
better O(n) solution exists using HashSet or HashMap
```

Example:

```txt
Two Sum asks for original indexes.
```

If you sort directly, original indexes may be lost.

So for original index problems, HashMap is usually better.

---

## Sorting vs HashSet vs HashMap

| Requirement | Better Pattern |
|---|---|
| Check duplicate only | HashSet or Sorting |
| Count frequency | HashMap |
| Need original index | HashMap |
| Need kth smallest/largest | Sorting |
| Need min difference | Sorting |
| Need pair sum values | Sorting + Two Pointers |
| Need order preserved | Avoid sorting |

---

## Time and Space Complexity

For `Arrays.sort(nums)`:

```txt
Time Complexity: O(n log n)
```

Usually, sorting-based solutions take:

```txt
O(n log n)
```

because sorting dominates the time.

Extra space depends on problem, but for beginner array problems, we usually mention:

```txt
Space Complexity: O(1) or O(n), depending on solution
```

---

## Basic Sorting Template

```java
import java.util.Arrays;

public void sortArray(int[] nums) {
    Arrays.sort(nums);
}
```

---

## Example 1: Contains Duplicate Using Sorting

Problem:

```txt
Check if array contains any duplicate.
```

Input:

```txt
nums = [1, 2, 3, 1]
```

Output:

```txt
true
```

Idea:

```txt
Sort the array.
If duplicate exists, duplicate values become adjacent.
Compare nums[i] with nums[i - 1].
```

Code:

```java
import java.util.Arrays;

class Solution {
    public boolean containsDuplicate(int[] nums) {
        Arrays.sort(nums);

        for (int i = 1; i < nums.length; i++) {
            if (nums[i] == nums[i - 1]) {
                return true;
            }
        }

        return false;
    }
}
```

---

## Dry Run: Contains Duplicate

```txt
nums = [1, 2, 3, 1]
```

After sorting:

```txt
[1, 1, 2, 3]
```

| i | nums[i - 1] | nums[i] | Check |
|---:|---:|---:|---|
| 1 | 1 | 1 | duplicate found |

Answer:

```txt
true
```

---

## Example 2: Count Unique Elements After Sorting

Problem:

```txt
Count unique elements in array.
```

Input:

```txt
nums = [4, 1, 2, 1, 2]
```

Output:

```txt
3
```

Unique elements:

```txt
1, 2, 4
```

Code:

```java
import java.util.Arrays;

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

## Why `count = 1`?

After sorting, if array is not empty, the first element is always counted as unique.

Example:

```txt
[1, 1, 2, 2, 4]
```

First `1` is counted.

Then we count only when current element is different from previous element.

---

## Example 3: Kth Smallest Element

Problem:

```txt
Find kth smallest element in array.
```

Input:

```txt
nums = [7, 10, 4, 3, 20, 15]
k = 3
```

Sorted:

```txt
[3, 4, 7, 10, 15, 20]
```

Output:

```txt
7
```

Code:

```java
import java.util.Arrays;

public int kthSmallest(int[] nums, int k) {
    Arrays.sort(nums);

    return nums[k - 1];
}
```

Why `k - 1`?

```txt
Because array index starts from 0.
```

So:

```txt
1st smallest → index 0
2nd smallest → index 1
3rd smallest → index 2
```

---

## Example 4: Kth Largest Element

Problem:

```txt
Find kth largest element in array.
```

Input:

```txt
nums = [7, 10, 4, 3, 20, 15]
k = 2
```

Sorted:

```txt
[3, 4, 7, 10, 15, 20]
```

Output:

```txt
15
```

Code:

```java
import java.util.Arrays;

public int kthLargest(int[] nums, int k) {
    Arrays.sort(nums);

    return nums[nums.length - k];
}
```

Why `nums.length - k`?

```txt
Last element is largest.
Second last element is second largest.
```

---

## Example 5: Minimum Difference Between Any Two Elements

Problem:

```txt
Find minimum difference between any two elements.
```

Input:

```txt
nums = [5, 3, 8, 1]
```

Sorted:

```txt
[1, 3, 5, 8]
```

Differences:

```txt
3 - 1 = 2
5 - 3 = 2
8 - 5 = 3
```

Output:

```txt
2
```

Code:

```java
import java.util.Arrays;

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

Why compare adjacent elements only?

```txt
After sorting, closest values will be next to each other.
```

---

## Example 6: Pair Sum After Sorting

Problem:

```txt
Check if any pair has sum equal to target.
Original indexes are not required.
```

Input:

```txt
nums = [8, 1, 6, 2]
target = 10
```

Sorted:

```txt
[1, 2, 6, 8]
```

Output:

```txt
true
```

Because:

```txt
2 + 8 = 10
```

Code:

```java
import java.util.Arrays;

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

Important:

```txt
Sorting + Two Pointers works well when original indexes are not needed.
```

---

## Example 7: Longest Consecutive Sequence Using Sorting

Problem:

```txt
Find length of longest consecutive sequence.
```

Input:

```txt
nums = [100, 4, 200, 1, 3, 2]
```

Sorted:

```txt
[1, 2, 3, 4, 100, 200]
```

Output:

```txt
4
```

Because:

```txt
1, 2, 3, 4
```

Code:

```java
import java.util.Arrays;

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

Important:

```txt
Skip duplicates while checking consecutive sequence.
```

---

## Example 8: Sort 0s, 1s, and 2s

Problem:

```txt
Sort array containing only 0, 1, and 2.
```

Input:

```txt
nums = [2, 0, 2, 1, 1, 0]
```

Output:

```txt
[0, 0, 1, 1, 2, 2]
```

Simple sorting solution:

```java
import java.util.Arrays;

public void sortColors(int[] nums) {
    Arrays.sort(nums);
}
```

Note:

```txt
This is the easiest solution.
Optimized Dutch National Flag pattern will come later.
```

---

## Sorting-Based Pattern Flow

Whenever you think sorting may help, follow this flow:

```txt
1. Check if order/index matters
2. If not, sort the array
3. Check what sorting gives you
4. Apply adjacent comparison / two pointers / kth logic
5. Analyze O(n log n) time
```

---

## Common Mistakes

### 1. Sorting When Original Index Is Needed

Problem:

```txt
Return original indexes of two numbers.
```

If you sort directly, original positions are lost.

Better:

```txt
Use HashMap
```

---

### 2. Forgetting Import

Correct:

```java
import java.util.Arrays;
```

---

### 3. Wrong Kth Index

For kth smallest:

```java
nums[k - 1]
```

For kth largest:

```java
nums[nums.length - k]
```

---

### 4. Comparing All Pairs After Sorting

For minimum difference, do not check every pair.

After sorting, compare only adjacent elements.

Correct:

```java
nums[i] - nums[i - 1]
```

---

### 5. Forgetting That Sorting Modifies Original Array

`Arrays.sort(nums)` changes the original array.

If original order is needed later, be careful.

---

## Beginner Checklist

Before applying Sorting-Based Pattern, ask:

```txt
1. Can I reorder the array?
2. Does original index matter?
3. Does sorting group duplicates together?
4. Does sorting help compare nearby values?
5. Can I use two pointers after sorting?
6. Do I need kth smallest or kth largest?
7. Is O(n log n) acceptable?
8. Will sorting destroy required order?
```

---

## Pattern Summary

| Point | Meaning |
|---|---|
| Pattern Name | Sorting-Based Patterns |
| Pattern Number | 08 |
| Used For | Order, duplicates, kth value, min difference, pair logic |
| Main Method | `Arrays.sort(nums)` |
| Time | Usually O(n log n) |
| Space | Depends on problem |
| Best When | Order/index does not matter |
| Avoid When | Original order/index is required |

---

## Next Pattern

```txt
Pattern 09: Merge Sorted Arrays
```
