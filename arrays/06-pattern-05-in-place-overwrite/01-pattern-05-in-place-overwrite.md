# Pattern 05: In-place Overwrite

In-place Overwrite is an array pattern where we modify the same array without creating another full array.

It is commonly used when the question asks us to:

```txt
remove elements
remove duplicates
move elements
keep valid elements
modify array in-place
return new length
```

---

## What Does In-place Mean?

In-place means:

```txt
Modify the original array itself
Do not create another full array
Use O(1) extra space
```

Example:

```txt
nums = [3, 2, 2, 3]
val = 3
```

Remove all `3`.

Expected result:

```txt
[2, 2, _, _]
```

We do not care about the remaining positions after valid elements.

The answer is:

```txt
new length = 2
```

---

## Why This Pattern Is Needed?

Many beginner solutions create a new array:

```java
int[] ans = new int[nums.length];
```

But some problems say:

```txt
Do it in-place
Use O(1) extra space
```

That means we should not create another array.

So we use the same array and overwrite valid values.

---

## Simple Meaning

```txt
Read each element
Keep only useful elements
Write useful elements at the front
Return how many useful elements are kept
```

---

## Main Idea

We use two positions:

| Pointer | Meaning |
|---|---|
| `i` | reads every element |
| `index` | writes valid elements |

Common names:

```java
int index = 0;
```

Then:

```txt
i checks every element
index stores where next valid element should go
```

---

## Pattern Signal

Think of In-place Overwrite when the question says:

```txt
remove element
remove duplicates
move zeroes
in-place
without extra space
return new length
modify nums directly
keep relative order
```

Most common signal:

```txt
Modify array in-place and return length
```

---

## How It Works

Example:

```txt
nums = [3, 2, 2, 3]
val = 3
```

We want to keep elements not equal to `3`.

Initial:

```txt
index = 0
```

Now scan:

| i | nums[i] | Keep? | Action | Array |
|---:|---:|---|---|---|
| 0 | 3 | No | skip | [3, 2, 2, 3] |
| 1 | 2 | Yes | nums[index] = 2, index++ | [2, 2, 2, 3] |
| 2 | 2 | Yes | nums[index] = 2, index++ | [2, 2, 2, 3] |
| 3 | 3 | No | skip | [2, 2, 2, 3] |

Final:

```txt
index = 2
```

Valid part:

```txt
[2, 2]
```

Return:

```txt
2
```

---

## Basic Template

```java
int index = 0;

for (int i = 0; i < nums.length; i++) {
    if (condition for valid element) {
        nums[index] = nums[i];
        index++;
    }
}

return index;
```

---

## Complete Java Code: Remove Element

Problem:

```txt
Remove all occurrences of val from nums in-place.
Return the new length.
```

Code:

```java
class Solution {
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
}
```

---

## Line-by-Line Explanation

```java
int index = 0;
```

`index` tells where the next valid element should be placed.

---

```java
for (int i = 0; i < nums.length; i++)
```

`i` reads every element from left to right.

---

```java
if (nums[i] != val)
```

This checks whether current element should be kept.

---

```java
nums[index] = nums[i];
```

Put the valid element at the correct front position.

---

```java
index++;
```

Move to the next writing position.

---

```java
return index;
```

`index` is the count of valid elements.

So it is also the new length.

---

## Why Return `index`?

Because `index` starts from `0` and increases only when we keep a valid element.

Example:

```txt
Valid elements = 2
index = 2
```

So return:

```txt
2
```

---

## Important Point

After in-place overwrite, the full array may look like this:

```txt
[2, 2, 2, 3]
```

But only the first `index` elements matter.

If returned length is `2`, valid part is:

```txt
[2, 2]
```

The remaining elements are ignored.

---

## Example 1: Remove Element

Input:

```txt
nums = [3, 2, 2, 3]
val = 3
```

Output:

```txt
2
```

Valid array part:

```txt
[2, 2]
```

Code:

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

---

## Example 2: Remove Duplicates from Sorted Array

Problem:

```txt
Given a sorted array, remove duplicates in-place.
Return number of unique elements.
```

Input:

```txt
nums = [1, 1, 2, 2, 3]
```

Output:

```txt
3
```

Valid array part:

```txt
[1, 2, 3]
```

Important condition:

```txt
Array is sorted
```

So duplicates come together.

Code:

```java
public int removeDuplicates(int[] nums) {
    if (nums.length == 0) {
        return 0;
    }

    int index = 1;

    for (int i = 1; i < nums.length; i++) {
        if (nums[i] != nums[i - 1]) {
            nums[index] = nums[i];
            index++;
        }
    }

    return index;
}
```

---

## Why `index = 1` Here?

In a sorted array, the first element is always unique.

Example:

```txt
[1, 1, 2, 2, 3]
```

We keep first `1` already.

So next unique element should be written at index `1`.

That is why:

```java
int index = 1;
```

---

## Dry Run: Remove Duplicates

```txt
nums = [1, 1, 2, 2, 3]
```

Initial:

```txt
index = 1
```

| i | nums[i] | nums[i - 1] | Unique? | Action | Valid Part |
|---:|---:|---:|---|---|---|
| 1 | 1 | 1 | No | skip | [1] |
| 2 | 2 | 1 | Yes | nums[1] = 2, index++ | [1, 2] |
| 3 | 2 | 2 | No | skip | [1, 2] |
| 4 | 3 | 2 | Yes | nums[2] = 3, index++ | [1, 2, 3] |

Final:

```txt
index = 3
```

Return:

```txt
3
```

---

## Example 3: Move Zeroes

Problem:

```txt
Move all zeroes to the end while keeping order of non-zero elements.
```

Input:

```txt
nums = [0, 1, 0, 3, 12]
```

Output:

```txt
[1, 3, 12, 0, 0]
```

Idea:

```txt
First place all non-zero elements at the front.
Then fill remaining positions with zero.
```

Code:

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

---

## Dry Run: Move Zeroes

```txt
nums = [0, 1, 0, 3, 12]
```

First pass keeps non-zero values:

| i | nums[i] | Keep? | Action | Array |
|---:|---:|---|---|---|
| 0 | 0 | No | skip | [0, 1, 0, 3, 12] |
| 1 | 1 | Yes | nums[0] = 1 | [1, 1, 0, 3, 12] |
| 2 | 0 | No | skip | [1, 1, 0, 3, 12] |
| 3 | 3 | Yes | nums[1] = 3 | [1, 3, 0, 3, 12] |
| 4 | 12 | Yes | nums[2] = 12 | [1, 3, 12, 3, 12] |

Now:

```txt
index = 3
```

Fill remaining with zero:

```txt
[1, 3, 12, 0, 0]
```

---

## In-place Overwrite vs Two Pointers

In-place Overwrite is related to Two Pointers, but the purpose is different.

| Point | Two Pointers | In-place Overwrite |
|---|---|---|
| Main idea | Use two positions smartly | Write valid elements at front |
| Common pointers | `left`, `right` | `i`, `index` |
| Used for | Pair sum, reverse, palindrome | Remove, keep, move, overwrite |
| Direction | Often from both ends | Usually left to right |
| Result | Find/check/swap | Modified array + new length |

---

## Time and Space Complexity

| Problem Type | Time | Space |
|---|---:|---:|
| Remove Element | O(n) | O(1) |
| Remove Duplicates | O(n) | O(1) |
| Move Zeroes | O(n) | O(1) |

Why time is O(n)?

```txt
We scan the array once or twice.
```

Why space is O(1)?

```txt
We modify the same array and use only extra variables.
```

---

## Common Mistakes

### 1. Creating Another Array

Wrong when question says in-place:

```java
int[] ans = new int[nums.length];
```

Correct:

```java
nums[index] = nums[i];
```

---

### 2. Returning Full Array Instead of Length

Many in-place problems ask:

```txt
Return new length
```

So return:

```java
return index;
```

Do not return the whole array if function expects `int`.

---

### 3. Forgetting to Increment `index`

Wrong:

```java
nums[index] = nums[i];
```

Correct:

```java
nums[index] = nums[i];
index++;
```

---

### 4. Comparing with Wrong Value

For remove element:

```java
nums[i] != val
```

For remove duplicates:

```java
nums[i] != nums[i - 1]
```

Do not mix both conditions.

---

### 5. Forgetting Sorted Condition

Remove duplicates using:

```java
nums[i] != nums[i - 1]
```

works because array is sorted.

If array is not sorted, duplicates may not be together.

---

### 6. Thinking Remaining Elements Matter

If returned length is `k`, only first `k` elements matter.

Example:

```txt
nums = [2, 2, 2, 3]
return = 2
```

Valid part:

```txt
[2, 2]
```

Remaining values do not matter.

---

## Beginner Checklist

Before applying In-place Overwrite, ask:

```txt
1. Does the question ask to modify array in-place?
2. Does it ask to return new length?
3. Which elements should be kept?
4. Which elements should be skipped?
5. What does index represent?
6. When should index increase?
7. Do remaining elements matter?
8. Is the array sorted?
9. Am I using O(1) extra space?
```

---

## Pattern Summary

| Point | Meaning |
|---|---|
| Pattern Name | In-place Overwrite |
| Pattern Number | 05 |
| Used For | Remove, keep, move, overwrite elements |
| Main Variables | `i`, `index` |
| Main Logic | Write valid elements at front |
| Time | Usually O(n) |
| Space | O(1) |
| Common Return | New length |
| Common Problems | Remove Element, Remove Duplicates, Move Zeroes |

---

## Next Pattern

```txt
Pattern 06: HashSet / Duplicate Detection
```
