# Pattern 17: Rotate, Dutch Flag, Product Except Self, Difference Array

This pattern contains four important array transformation techniques:

```txt
1. Rotate Array
2. Dutch National Flag
3. Product Except Self
4. Difference Array
```

These patterns are commonly used when the array needs to be rearranged, modified, or updated efficiently.

---

## Why These Patterns Are Grouped Together?

These are not simple searching or counting patterns.

They are array manipulation patterns.

They are used when the question says:

```txt
rotate array
sort 0s, 1s, 2s
product except self
range update
modify array efficiently
without extra space
without division
in-place
```

---

# Part 1: Rotate Array

## What Is Rotate Array?

Rotating an array means shifting elements in a circular way.

Example:

```txt
nums = [1, 2, 3, 4, 5, 6, 7]
k = 3
```

Rotate right by `3`:

```txt
[5, 6, 7, 1, 2, 3, 4]
```

The last `3` elements move to the front.

---

## Simple Meaning

```txt
Right rotation:
Elements move towards the right.
Last elements come to the front.

Left rotation:
Elements move towards the left.
First elements go to the end.
```

---

## Pattern Signal

Think of Rotate Array when the question says:

```txt
rotate array
shift elements
right rotate
left rotate
circular movement
rotate by k steps
```

---

## Important Point About k

If `k` is larger than array length, use:

```java
k = k % nums.length;
```

Example:

```txt
n = 7
k = 10
```

Rotating by `10` is same as rotating by:

```txt
10 % 7 = 3
```

---

## Rotate Right Using Reverse Method

For right rotation:

```txt
nums = [1, 2, 3, 4, 5, 6, 7]
k = 3
```

Steps:

```txt
1. Reverse whole array
   [7, 6, 5, 4, 3, 2, 1]

2. Reverse first k elements
   [5, 6, 7, 4, 3, 2, 1]

3. Reverse remaining elements
   [5, 6, 7, 1, 2, 3, 4]
```

---

## Complete Java Code: Rotate Right

```java
class Solution {
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
}
```

---

## Line-by-Line Explanation

```java
int n = nums.length;
```

Stores array length.

---

```java
k = k % n;
```

Handles cases where `k` is greater than array size.

---

```java
reverse(nums, 0, n - 1);
```

Reverses the full array.

---

```java
reverse(nums, 0, k - 1);
```

Fixes the first `k` elements.

---

```java
reverse(nums, k, n - 1);
```

Fixes the remaining elements.

---

## Dry Run: Rotate Right

```txt
nums = [1, 2, 3, 4, 5, 6, 7]
k = 3
```

| Step | Operation | Array |
|---:|---|---|
| 1 | Original | [1, 2, 3, 4, 5, 6, 7] |
| 2 | Reverse full array | [7, 6, 5, 4, 3, 2, 1] |
| 3 | Reverse first k elements | [5, 6, 7, 4, 3, 2, 1] |
| 4 | Reverse remaining elements | [5, 6, 7, 1, 2, 3, 4] |

Answer:

```txt
[5, 6, 7, 1, 2, 3, 4]
```

---

# Part 2: Dutch National Flag

## What Is Dutch National Flag Pattern?

Dutch National Flag is used to sort an array containing only:

```txt
0, 1, and 2
```

Example:

```txt
nums = [2, 0, 2, 1, 1, 0]
```

Output:

```txt
[0, 0, 1, 1, 2, 2]
```

---

## Why Not Just Sort?

We can use:

```java
Arrays.sort(nums);
```

But that takes:

```txt
O(n log n)
```

Dutch National Flag solves it in:

```txt
O(n)
```

and modifies array in-place.

---

## Pattern Signal

Think of Dutch National Flag when the question says:

```txt
sort 0s 1s 2s
sort colors
three types of elements
low mid high
in-place sorting
linear time sorting
```

Most common signal:

```txt
Array contains only 0, 1, and 2.
```

---

## Main Idea

Use three pointers:

| Pointer | Meaning |
|---|---|
| `low` | next position for 0 |
| `mid` | current element being checked |
| `high` | next position for 2 |

Initial:

```java
int low = 0;
int mid = 0;
int high = nums.length - 1;
```

---

## Rules

| nums[mid] | Action |
|---:|---|
| 0 | swap with low, low++, mid++ |
| 1 | mid++ |
| 2 | swap with high, high-- |

Important:

```txt
When nums[mid] == 2, do not increment mid immediately.
```

Why?

Because after swapping with `high`, the new value at `mid` is unknown.

---

## Complete Java Code: Sort Colors

```java
class Solution {
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
}
```

---

## Dry Run: Dutch National Flag

```txt
nums = [2, 0, 2, 1, 1, 0]
```

Initial:

```txt
low = 0
mid = 0
high = 5
```

| Step | nums[mid] | Action | Array |
|---:|---:|---|---|
| 1 | 2 | swap mid and high, high-- | [0, 0, 2, 1, 1, 2] |
| 2 | 0 | swap low and mid, low++, mid++ | [0, 0, 2, 1, 1, 2] |
| 3 | 0 | swap low and mid, low++, mid++ | [0, 0, 2, 1, 1, 2] |
| 4 | 2 | swap mid and high, high-- | [0, 0, 1, 1, 2, 2] |
| 5 | 1 | mid++ | [0, 0, 1, 1, 2, 2] |
| 6 | 1 | mid++ | [0, 0, 1, 1, 2, 2] |

Final:

```txt
[0, 0, 1, 1, 2, 2]
```

---

# Part 3: Product Except Self

## What Is Product Except Self?

Product Except Self means:

```txt
For every index i, return product of all elements except nums[i].
```

Example:

```txt
nums = [1, 2, 3, 4]
```

Output:

```txt
[24, 12, 8, 6]
```

Explanation:

```txt
answer[0] = 2 * 3 * 4 = 24
answer[1] = 1 * 3 * 4 = 12
answer[2] = 1 * 2 * 4 = 8
answer[3] = 1 * 2 * 3 = 6
```

---

## Pattern Signal

Think of Product Except Self when the question says:

```txt
product except self
without division
prefix product
suffix product
product of all elements except current
```

Most common signal:

```txt
Do not use division.
```

---

## Main Idea

For each index:

```txt
answer[i] = product of elements on left side * product of elements on right side
```

Example:

```txt
nums = [1, 2, 3, 4]
```

For index `2`:

```txt
left product = 1 * 2 = 2
right product = 4
answer[2] = 2 * 4 = 8
```

---

## Prefix and Suffix Logic

Instead of creating two arrays, we can use the answer array itself.

Step 1: Store prefix product in answer.

Step 2: Multiply suffix product from right side.

---

## Complete Java Code: Product Except Self

```java
class Solution {
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
}
```

---

## Line-by-Line Explanation

```java
int[] answer = new int[n];
```

Stores final product result.

---

```java
int prefix = 1;
```

Before the first element, left product is `1`.

---

```java
answer[i] = prefix;
```

Stores product of all elements before index `i`.

---

```java
prefix = prefix * nums[i];
```

Updates prefix for next index.

---

```java
int suffix = 1;
```

After the last element, right product is `1`.

---

```java
answer[i] = answer[i] * suffix;
```

Multiplies left product with right product.

---

```java
suffix = suffix * nums[i];
```

Updates suffix for next index on the left.

---

## Dry Run: Product Except Self

```txt
nums = [1, 2, 3, 4]
```

First pass: prefix products

| i | prefix before | answer[i] | prefix after |
|---:|---:|---:|---:|
| 0 | 1 | 1 | 1 |
| 1 | 1 | 1 | 2 |
| 2 | 2 | 2 | 6 |
| 3 | 6 | 6 | 24 |

After first pass:

```txt
answer = [1, 1, 2, 6]
```

Second pass: suffix products

| i | suffix before | answer[i] after multiply | suffix after |
|---:|---:|---:|---:|
| 3 | 1 | 6 | 4 |
| 2 | 4 | 8 | 12 |
| 1 | 12 | 12 | 24 |
| 0 | 24 | 24 | 24 |

Final:

```txt
[24, 12, 8, 6]
```

---

## Why It Handles Zeroes

Example:

```txt
nums = [1, 2, 0, 4]
```

Division-based approach can fail because division by zero is not allowed.

Prefix-suffix method still works correctly.

That is why this pattern is preferred.

---

# Part 4: Difference Array

## What Is Difference Array?

Difference Array is used when we need to apply many range updates efficiently.

Example:

```txt
Add 5 from index 1 to index 3
```

Normal way:

```txt
nums[1] += 5
nums[2] += 5
nums[3] += 5
```

If there are many updates, this becomes slow.

Difference Array helps apply each range update in:

```txt
O(1)
```

Then we rebuild the final array using prefix sum.

---

## Pattern Signal

Think of Difference Array when the question says:

```txt
range update
add value from l to r
multiple updates
increment subarray
range addition
queries update array
```

Most common signal:

```txt
Many range updates
```

---

## Main Idea

To add `value` from index `left` to `right`:

```java
diff[left] += value;

if (right + 1 < n) {
    diff[right + 1] -= value;
}
```

Then build final array using prefix sum.

---

## Why This Works?

When we add at `left`, the effect starts.

```txt
diff[left] += value
```

When we subtract after `right`, the effect stops.

```txt
diff[right + 1] -= value
```

Then prefix sum spreads the effect across the range.

---

## Complete Java Code: Range Update

Problem:

```txt
Given length n and updates [left, right, value],
return final array after applying all updates.
```

Code:

```java
class Solution {
    public int[] rangeUpdate(int n, int[][] updates) {
        int[] diff = new int[n];

        for (int i = 0; i < updates.length; i++) {
            int left = updates[i][0];
            int right = updates[i][1];
            int value = updates[i][2];

            diff[left] += value;

            if (right + 1 < n) {
                diff[right + 1] -= value;
            }
        }

        int[] result = new int[n];
        result[0] = diff[0];

        for (int i = 1; i < n; i++) {
            result[i] = result[i - 1] + diff[i];
        }

        return result;
    }
}
```

---

## Dry Run: Difference Array

```txt
n = 5
updates = [
  [1, 3, 2],
  [2, 4, 3]
]
```

Initial:

```txt
diff = [0, 0, 0, 0, 0]
```

Update 1:

```txt
left = 1, right = 3, value = 2
diff[1] += 2
diff[4] -= 2
```

Now:

```txt
diff = [0, 2, 0, 0, -2]
```

Update 2:

```txt
left = 2, right = 4, value = 3
diff[2] += 3
right + 1 = 5, out of range
```

Now:

```txt
diff = [0, 2, 3, 0, -2]
```

Build prefix:

| i | result[i] |
|---:|---:|
| 0 | 0 |
| 1 | 2 |
| 2 | 5 |
| 3 | 5 |
| 4 | 3 |

Final array:

```txt
[0, 2, 5, 5, 3]
```

---

## Difference Array vs Prefix Sum

| Point | Prefix Sum | Difference Array |
|---|---|---|
| Used for | Fast range sum queries | Fast range updates |
| Query type | Sum from l to r | Add value to l to r |
| Preprocessing | Build prefix | Build diff |
| Final step | Direct query | Reconstruct using prefix |
| Main idea | Store previous sums | Store changes |

---

## Time and Space Complexity

| Pattern | Time | Space |
|---|---:|---:|
| Rotate Array | O(n) | O(1) |
| Dutch National Flag | O(n) | O(1) |
| Product Except Self | O(n) | O(1) extra excluding answer |
| Difference Array | O(n + q) | O(n) |

Here `q` is number of updates.

---

## Common Mistakes

### 1. Forgetting `k = k % n` in Rotate Array

If `k` is larger than array length, rotation may be wrong.

Correct:

```java
k = k % nums.length;
```

---

### 2. Incrementing `mid` After Swapping With `high`

Wrong in Dutch Flag:

```java
swap(nums, mid, high);
mid++;
high--;
```

Correct:

```java
swap(nums, mid, high);
high--;
```

Do not increment `mid` because swapped element is unknown.

---

### 3. Using Division in Product Except Self

Problem says:

```txt
without division
```

So use prefix and suffix products.

---

### 4. Starting Prefix Product With 0

Wrong:

```java
int prefix = 0;
```

Correct:

```java
int prefix = 1;
```

Because multiplication identity is `1`.

---

### 5. Forgetting Difference Array Boundary Check

Wrong:

```java
diff[right + 1] -= value;
```

This can cause index out of bounds.

Correct:

```java
if (right + 1 < n) {
    diff[right + 1] -= value;
}
```

---

## Beginner Checklist

Before applying these patterns, ask:

```txt
1. Is the question asking to rotate the array?
2. Does the array contain only 0, 1, and 2?
3. Does the question ask product except self?
4. Is division forbidden?
5. Are there many range updates?
6. Can reverse help rotate in-place?
7. Can low-mid-high help sort three values?
8. Can prefix and suffix products solve product except self?
9. Can difference array make range updates O(1)?
10. What is the required time and space complexity?
```

---

## Pattern Summary

| Sub-Pattern | Used For | Main Logic |
|---|---|---|
| Rotate Array | Circular shifting | Reverse full + parts |
| Dutch National Flag | Sort 0s, 1s, 2s | low, mid, high pointers |
| Product Except Self | Product without division | Prefix × suffix |
| Difference Array | Range updates | Start effect, stop effect |

---

## Next Pattern

```txt
Pattern 18: Matrix and Final Checklist
```
