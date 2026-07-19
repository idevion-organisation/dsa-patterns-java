# Pattern 16: XOR and Math Formula

XOR and Math Formula is an array pattern used when the problem has a clear number property.

This pattern is commonly used for:

```txt
single number
missing number
duplicate/missing logic
number appearing once
range 0 to n
range 1 to n
sum formula
xor cancellation
```

---

## What Is XOR?

XOR is a bitwise operator.

In Java, XOR is written as:

```java
^
```

Example:

```java
int result = 5 ^ 3;
```

For DSA, we mostly use XOR because it has a very useful cancellation property.

---

## Important XOR Rules

| Rule | Meaning |
|---|---|
| `x ^ x = 0` | Same numbers cancel each other |
| `x ^ 0 = x` | XOR with 0 gives same number |
| `x ^ y = y ^ x` | Order does not matter |
| `(x ^ y) ^ z = x ^ (y ^ z)` | Grouping does not matter |

Most important rule:

```txt
Same numbers cancel out.
```

Example:

```txt
5 ^ 5 = 0
```

Another example:

```txt
2 ^ 3 ^ 2
```

Rearrange:

```txt
2 ^ 2 ^ 3 = 0 ^ 3 = 3
```

So answer is:

```txt
3
```

---

## Simple Meaning of XOR Pattern

```txt
If every number appears twice except one number,
XOR all numbers.
Pairs cancel out.
The remaining number is the answer.
```

---

## Pattern Signal

Think of XOR when the question says:

```txt
every element appears twice except one
find single number
find missing number
numbers are in range 0 to n
numbers are in range 1 to n
constant extra space
linear time
without extra space
```

Most common signal:

```txt
Every number appears twice except one.
```

---

## What Is Math Formula Pattern?

Math Formula Pattern is used when the array contains numbers from a known range.

Example:

```txt
numbers are from 0 to n
numbers are from 1 to n
one number is missing
```

Then we can use formulas like:

```txt
sum of 0 to n = n * (n + 1) / 2
sum of 1 to n = n * (n + 1) / 2
```

---

## XOR vs Math Formula

| Point | XOR | Math Formula |
|---|---|---|
| Main idea | Same numbers cancel | Expected sum - actual sum |
| Used for | Single number, missing number | Missing number, range problems |
| Handles overflow risk | Better | Can overflow if numbers are large |
| Extra space | O(1) | O(1) |
| Time | O(n) | O(n) |

For missing number, both XOR and Math Formula work.

---

## Example 1: Single Number

Problem:

```txt
Every element appears twice except one.
Find the single number.
```

Input:

```txt
nums = [4, 1, 2, 1, 2]
```

Output:

```txt
4
```

Because:

```txt
1 appears twice
2 appears twice
4 appears once
```

---

## Brute Force Idea

For each number, count how many times it appears.

This may take:

```txt
O(n²)
```

Or we can use HashMap:

```txt
O(n) time and O(n) space
```

But XOR gives:

```txt
O(n) time and O(1) space
```

---

## Complete Java Code: Single Number

```java
class Solution {
    public int singleNumber(int[] nums) {
        int xor = 0;

        for (int i = 0; i < nums.length; i++) {
            xor = xor ^ nums[i];
        }

        return xor;
    }
}
```

---

## Line-by-Line Explanation

```java
int xor = 0;
```

Start with 0 because:

```txt
x ^ 0 = x
```

---

```java
for (int i = 0; i < nums.length; i++)
```

Traverse every element.

---

```java
xor = xor ^ nums[i];
```

XOR current number with previous result.

---

```java
return xor;
```

All duplicate pairs cancel out.

The remaining value is the single number.

---

## Dry Run: Single Number

```txt
nums = [4, 1, 2, 1, 2]
```

| i | nums[i] | xor before | Operation | xor after |
|---:|---:|---:|---|---:|
| 0 | 4 | 0 | 0 ^ 4 | 4 |
| 1 | 1 | 4 | 4 ^ 1 | 5 |
| 2 | 2 | 5 | 5 ^ 2 | 7 |
| 3 | 1 | 7 | 7 ^ 1 | 6 |
| 4 | 2 | 6 | 6 ^ 2 | 4 |

Final answer:

```txt
4
```

Better way to understand:

```txt
4 ^ 1 ^ 2 ^ 1 ^ 2
= 4 ^ (1 ^ 1) ^ (2 ^ 2)
= 4 ^ 0 ^ 0
= 4
```

---

## Example 2: Missing Number Using Math Formula

Problem:

```txt
Given nums containing numbers from 0 to n.
One number is missing.
Find the missing number.
```

Input:

```txt
nums = [3, 0, 1]
```

Here:

```txt
n = 3
Range = 0 to 3
Expected numbers = [0, 1, 2, 3]
```

Missing number:

```txt
2
```

---

## Math Formula Logic

Expected sum:

```txt
0 + 1 + 2 + 3 = 6
```

Actual sum:

```txt
3 + 0 + 1 = 4
```

Missing number:

```txt
6 - 4 = 2
```

Formula:

```txt
expectedSum = n * (n + 1) / 2
missing = expectedSum - actualSum
```

---

## Complete Java Code: Missing Number Using Formula

```java
class Solution {
    public int missingNumber(int[] nums) {
        int n = nums.length;

        int expectedSum = n * (n + 1) / 2;
        int actualSum = 0;

        for (int i = 0; i < nums.length; i++) {
            actualSum += nums[i];
        }

        return expectedSum - actualSum;
    }
}
```

---

## Safer Version Using long

If numbers are large, sum can overflow `int`.

Safer code:

```java
class Solution {
    public int missingNumber(int[] nums) {
        int n = nums.length;

        long expectedSum = (long) n * (n + 1) / 2;
        long actualSum = 0;

        for (int i = 0; i < nums.length; i++) {
            actualSum += nums[i];
        }

        return (int) (expectedSum - actualSum);
    }
}
```

---

## Example 3: Missing Number Using XOR

Same problem:

```txt
nums = [3, 0, 1]
```

Range:

```txt
0 to 3
```

Expected numbers:

```txt
0, 1, 2, 3
```

Array numbers:

```txt
3, 0, 1
```

If we XOR both sides:

```txt
0 ^ 1 ^ 2 ^ 3 ^ 3 ^ 0 ^ 1
```

Same numbers cancel:

```txt
0 cancels 0
1 cancels 1
3 cancels 3
```

Remaining:

```txt
2
```

Code:

```java
class Solution {
    public int missingNumber(int[] nums) {
        int xor = nums.length;

        for (int i = 0; i < nums.length; i++) {
            xor = xor ^ i;
            xor = xor ^ nums[i];
        }

        return xor;
    }
}
```

---

## Dry Run: Missing Number Using XOR

```txt
nums = [3, 0, 1]
n = 3
```

Initial:

```txt
xor = 3
```

| i | nums[i] | Operation | xor meaning |
|---:|---:|---|---|
| 0 | 3 | xor ^ 0 ^ 3 | 3 cancels with 3 |
| 1 | 0 | xor ^ 1 ^ 0 | 0 cancels with 0 |
| 2 | 1 | xor ^ 2 ^ 1 | 1 cancels with 1 |

Remaining:

```txt
2
```

Answer:

```txt
2
```

---

## Example 4: Find Duplicate and Missing Number Using Math

Problem:

```txt
Array contains numbers from 1 to n.
One number is repeated.
One number is missing.
Find both.
```

Input:

```txt
nums = [1, 2, 2, 4]
```

Expected:

```txt
[1, 2, 3, 4]
```

Duplicate:

```txt
2
```

Missing:

```txt
3
```

Beginner-friendly way is to use frequency array.

Code:

```java
public int[] findDuplicateAndMissing(int[] nums) {
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

This is not pure O(1) space, but it is easiest and safest for beginners.

---

## Example 5: Good Pairs Using Math Formula

Problem:

```txt
Count pairs where nums[i] == nums[j] and i < j.
```

Input:

```txt
nums = [1, 2, 3, 1, 1, 3]
```

Equal groups:

```txt
1 appears 3 times
3 appears 2 times
```

Number of pairs from frequency `f`:

```txt
f * (f - 1) / 2
```

For `1`:

```txt
3 * 2 / 2 = 3
```

For `3`:

```txt
2 * 1 / 2 = 1
```

Total:

```txt
4
```

Code:

```java
import java.util.HashMap;

public int numIdenticalPairs(int[] nums) {
    HashMap<Integer, Integer> map = new HashMap<>();

    for (int i = 0; i < nums.length; i++) {
        map.put(nums[i], map.getOrDefault(nums[i], 0) + 1);
    }

    int count = 0;

    for (int key : map.keySet()) {
        int freq = map.get(key);
        count += freq * (freq - 1) / 2;
    }

    return count;
}
```

---

## Example 6: Number Appearing Once When Others Appear Twice

This is the classic XOR problem.

Input:

```txt
nums = [2, 2, 1]
```

Output:

```txt
1
```

Code:

```java
public int singleNumber(int[] nums) {
    int xor = 0;

    for (int i = 0; i < nums.length; i++) {
        xor ^= nums[i];
    }

    return xor;
}
```

---

## Important Warning: When XOR Does Not Directly Work

XOR works directly when:

```txt
Every duplicate appears exactly twice
Only one number appears once
```

But XOR does not directly solve every duplicate problem.

Example:

```txt
Find duplicate when duplicate may appear more than twice
```

In that case, use:

```txt
HashSet
HashMap
Binary Search
Floyd cycle detection
```

depending on constraints.

So always check the exact condition.

---

## Common Math Formulas

| Formula | Use |
|---|---|
| `n * (n + 1) / 2` | Sum from 1 to n or 0 to n |
| `freq * (freq - 1) / 2` | Number of pairs from same frequency |
| `right - left + 1` | Length of subarray/window |
| `n - k` | kth largest index after sorting |
| `k - 1` | kth smallest index after sorting |

---

## Time and Space Complexity

For Single Number using XOR:

| Complexity | Value |
|---|---:|
| Time Complexity | O(n) |
| Space Complexity | O(1) |

For Missing Number using formula:

| Complexity | Value |
|---|---:|
| Time Complexity | O(n) |
| Space Complexity | O(1) |

For frequency-based duplicate/missing:

| Complexity | Value |
|---|---:|
| Time Complexity | O(n) |
| Space Complexity | O(n) |

---

## Common Mistakes

### 1. Using XOR When Conditions Do Not Match

XOR cancellation works only when pairs cancel properly.

If numbers do not appear exactly twice, be careful.

---

### 2. Forgetting That XOR Order Does Not Matter

This is correct:

```txt
2 ^ 1 ^ 2 = 1
```

Because:

```txt
2 ^ 2 ^ 1 = 1
```

---

### 3. Overflow in Sum Formula

Wrong for very large `n`:

```java
int expectedSum = n * (n + 1) / 2;
```

Safer:

```java
long expectedSum = (long) n * (n + 1) / 2;
```

---

### 4. Confusing Range 0 to n and 1 to n

For missing number problem:

```txt
nums length = n
range = 0 to n
```

For many other problems:

```txt
nums length = n
range = 1 to n
```

Always read the range carefully.

---

### 5. Sorting When Math or XOR Is Enough

If the problem can be solved in O(n) and O(1), avoid unnecessary sorting.

Sorting takes:

```txt
O(n log n)
```

---

## Beginner Checklist

Before applying XOR or Math Formula, ask:

```txt
1. Are numbers in a known range?
2. Is one number missing?
3. Does every duplicate appear exactly twice?
4. Is one number appearing once?
5. Can XOR cancellation help?
6. Can sum formula help?
7. Can sum overflow int?
8. Is the range 0 to n or 1 to n?
9. Do I need count/frequency instead?
10. Is XOR condition strictly valid?
```

---

## Pattern Summary

| Point | Meaning |
|---|---|
| Pattern Name | XOR and Math Formula |
| Pattern Number | 16 |
| Used For | Single number, missing number, range formula |
| Main XOR Rule | `x ^ x = 0`, `x ^ 0 = x` |
| Main Formula | `n * (n + 1) / 2` |
| Time | Usually O(n) |
| Space | Usually O(1) |
| Best Signal | Pairs cancel / one missing / known range |

---

## Next Pattern

```txt
Pattern 17: Rotate, Dutch Flag, Product Except Self, Difference Array
```
