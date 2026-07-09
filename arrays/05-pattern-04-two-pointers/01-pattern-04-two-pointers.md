# Pattern 04: Two Pointers

Two Pointers is an array pattern where we use two variables to point to two different positions in the array.

Instead of checking every possible pair using nested loops, we move two pointers smartly to reduce time complexity.

---

## What Is Two Pointers?

Two Pointers means using two indexes to solve the problem.

Common pointer names:

```java
int left = 0;
int right = nums.length - 1;
```

Here:

```txt
left  → starts from beginning
right → starts from end
```

Then we move them based on conditions.

---

## Simple Meaning

```txt
Use two indexes
Check elements at both indexes
Move one pointer or both pointers
Stop when condition becomes false
```

Example:

```txt
nums = [1, 2, 4, 6, 8]
target = 10
```

We want to check if any pair gives sum `10`.

Start:

```txt
left = 0  → nums[left] = 1
right = 4 → nums[right] = 8
```

Sum:

```txt
1 + 8 = 9
```

Since `9 < 10`, we need a bigger sum.

Move `left` forward.

Now:

```txt
left = 1  → nums[left] = 2
right = 4 → nums[right] = 8
```

Sum:

```txt
2 + 8 = 10
```

Pair found.

---

## Most Important Condition

Two Pointers is most powerful when:

```txt
Array is sorted
```

Especially for pair-sum type problems.

Example sorted array:

```txt
[1, 2, 4, 6, 8]
```

If the array is sorted:

```txt
small values are on the left
large values are on the right
```

So we can decide which pointer to move.

---

## When to Use Two Pointers?

Use Two Pointers when the problem talks about:

```txt
pair
two numbers
sorted array
target sum
reverse array
palindrome-style checking
remove or compare from both sides
left and right side comparison
```

Most common beginner signal:

```txt
Sorted array + pair sum = Two Pointers
```

---

## Pattern Signal

If the question contains words like:

```txt
pair
two elements
target sum
sorted array
reverse
from both ends
left and right
closest pair
palindrome
```

Think:

```txt
Two Pointers
```

---

## Why Not Use Nested Loops?

Brute force checks every pair.

Example:

```java
for (int i = 0; i < nums.length; i++) {
    for (int j = i + 1; j < nums.length; j++) {
        if (nums[i] + nums[j] == target) {
            return true;
        }
    }
}
```

Time:

```txt
O(n²)
```

Two Pointers can solve sorted pair-sum in:

```txt
O(n)
```

That is the main advantage.

---

## Main Types of Two Pointers

There are two common types.

| Type | Pointer Movement | Used For |
|---|---|---|
| Opposite Direction | `left` starts at beginning, `right` starts at end | Pair sum, reverse, palindrome |
| Same Direction | both pointers move from left to right | Remove duplicates, move elements, slow-fast logic |

In this pattern, we mainly focus on:

```txt
Opposite Direction Two Pointers
```

Same direction will be used more deeply in the next pattern:

```txt
Pattern 05: In-place Overwrite
```

---

## Type 1: Opposite Direction Two Pointers

Start:

```java
int left = 0;
int right = nums.length - 1;
```

Move while:

```java
while (left < right)
```

Why `left < right`?

Because we need two different elements.

If `left == right`, both pointers are on the same element.

---

## Core Logic for Pair Sum

For sorted array pair sum:

```txt
sum = nums[left] + nums[right]
```

Three cases:

```txt
sum == target → pair found
sum < target  → need bigger sum, move left
sum > target  → need smaller sum, move right
```

In Java:

```java
if (sum == target) {
    return true;
}
else if (sum < target) {
    left++;
}
else {
    right--;
}
```

---

## Complete Java Code: Pair Sum Exists

```java
class Solution {
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
}
```

---

## Line-by-Line Explanation

```java
int left = 0;
```

`left` starts from the first index.

```java
int right = nums.length - 1;
```

`right` starts from the last index.

```java
while (left < right)
```

Loop runs while both pointers are on different elements.

```java
int sum = nums[left] + nums[right];
```

Calculate the pair sum.

```java
if (sum == target)
```

If sum is equal to target, pair exists.

```java
return true;
```

Return true immediately.

```java
else if (sum < target)
```

If sum is smaller than target, we need a bigger value.

```java
left++;
```

Move left pointer forward.

```java
else
```

If sum is greater than target, we need a smaller value.

```java
right--;
```

Move right pointer backward.

```java
return false;
```

If loop ends, no valid pair exists.

---

## Dry Run 1: Pair Found

```txt
nums = [1, 2, 4, 6, 8]
target = 10
```

Initial values:

```txt
left = 0
right = 4
```

| Step | left | right | nums[left] | nums[right] | sum | Decision |
|---:|---:|---:|---:|---:|---:|---|
| 1 | 0 | 4 | 1 | 8 | 9 | 9 < 10, move left |
| 2 | 1 | 4 | 2 | 8 | 10 | pair found |

Answer:

```txt
true
```

---

## Dry Run 2: Pair Not Found

```txt
nums = [1, 2, 4, 6, 8]
target = 20
```

| Step | left | right | nums[left] | nums[right] | sum | Decision |
|---:|---:|---:|---:|---:|---:|---|
| 1 | 0 | 4 | 1 | 8 | 9 | 9 < 20, move left |
| 2 | 1 | 4 | 2 | 8 | 10 | 10 < 20, move left |
| 3 | 2 | 4 | 4 | 8 | 12 | 12 < 20, move left |
| 4 | 3 | 4 | 6 | 8 | 14 | 14 < 20, move left |

Now:

```txt
left = 4
right = 4
```

Condition:

```txt
left < right
4 < 4 → false
```

Answer:

```txt
false
```

---

## Example 1: Return Pair Indexes

Problem:

```txt
Return indexes of two numbers whose sum is target.
Array is sorted.
```

Input:

```txt
nums = [1, 2, 4, 6, 8]
target = 10
```

Output:

```txt
[1, 4]
```

Because:

```txt
nums[1] + nums[4] = 2 + 8 = 10
```

Code:

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

---

## Example 2: Reverse an Array

Two Pointers is also used to reverse an array.

Input:

```txt
nums = [1, 2, 3, 4]
```

Output:

```txt
[4, 3, 2, 1]
```

Idea:

```txt
Swap left and right
Move both pointers inward
```

Code:

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

---

## Dry Run: Reverse Array

```txt
nums = [1, 2, 3, 4]
```

| Step | left | right | Action | Array |
|---:|---:|---:|---|---|
| 1 | 0 | 3 | swap 1 and 4 | [4, 2, 3, 1] |
| 2 | 1 | 2 | swap 2 and 3 | [4, 3, 2, 1] |

Now:

```txt
left = 2
right = 1
```

Loop stops.

Final array:

```txt
[4, 3, 2, 1]
```

---

## Example 3: Check Palindrome Style Array

Problem:

```txt
Check if array reads same from start and end.
```

Input:

```txt
nums = [1, 2, 3, 2, 1]
```

Output:

```txt
true
```

Code:

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

## Example 4: Squares of Sorted Array

Problem:

```txt
Given a sorted array, return squares in sorted order.
```

Input:

```txt
nums = [-4, -1, 0, 3, 10]
```

Output:

```txt
[0, 1, 9, 16, 100]
```

Why Two Pointers?

Negative numbers can become large after squaring.

```txt
-4 squared = 16
10 squared = 100
```

The largest square will be at either left side or right side.

Code:

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

Important:

```txt
We fill answer array from the end because largest square comes first.
```

---

## Time and Space Complexity

For pair sum:

| Complexity | Value |
|---|---:|
| Time Complexity | O(n) |
| Space Complexity | O(1) |

Why time is `O(n)`?

```txt
Each pointer moves at most n times total.
```

Why space is `O(1)`?

```txt
Only left, right, and sum variables are used.
```

For sorted squares:

| Complexity | Value |
|---|---:|
| Time Complexity | O(n) |
| Space Complexity | O(n) |

Because we create a new answer array.

---

## Two Pointers vs Nested Loops

| Point | Nested Loops | Two Pointers |
|---|---|---|
| Checks | Every pair | Smart pair movement |
| Time | O(n²) | O(n) |
| Works best when | No structure | Array is sorted / two-side logic |
| Beginner signal | Try all pairs | Sorted pair / opposite ends |

---

## Common Mistakes

### 1. Using Two Pointers on Unsorted Pair Sum

Wrong:

```txt
nums = [8, 1, 6, 2]
target = 10
```

Direct Two Pointers will not work correctly.

Correct:

```txt
Use Two Pointers when array is sorted.
```

If array is not sorted, think:

```txt
HashMap
```

or sort if indexes are not required.

---

### 2. Wrong Loop Condition

For pair problems, use:

```java
while (left < right)
```

Because pair needs two different elements.

Do not use:

```java
while (left <= right)
```

for pair sum, because it may use the same element twice.

---

### 3. Moving Wrong Pointer

If sum is smaller:

```java
left++;
```

If sum is larger:

```java
right--;
```

Do not reverse this logic.

---

### 4. Forgetting to Move Pointers

Wrong:

```java
while (left < right) {
    int sum = nums[left] + nums[right];

    if (sum < target) {
        // forgot left++
    }
}
```

This causes infinite loop.

---

### 5. Confusing Index and Value

If question asks for indexes:

```java
return new int[]{left, right};
```

If question asks for values:

```java
return new int[]{nums[left], nums[right]};
```

Read the question carefully.

---

## Beginner Checklist

Before applying Two Pointers, ask:

```txt
1. Is the array sorted?
2. Is the problem about pair or two elements?
3. Do I need indexes or values?
4. Should pointers start from both ends?
5. What should happen if sum is smaller?
6. What should happen if sum is larger?
7. Should I use left < right or left <= right?
8. Can I solve this without nested loops?
```

---

## Pattern Summary

| Point | Meaning |
|---|---|
| Pattern Name | Two Pointers |
| Pattern Number | 04 |
| Used For | Pair sum, reverse, palindrome, two-side comparison |
| Best Condition | Sorted array or two-side logic |
| Main Variables | `left`, `right` |
| Common Loop | `while (left < right)` |
| Time | Usually O(n) |
| Space | Usually O(1) |
| Main Benefit | Avoids unnecessary nested loops |

---

## Next Pattern

```txt
Pattern 05: In-place Overwrite
```
