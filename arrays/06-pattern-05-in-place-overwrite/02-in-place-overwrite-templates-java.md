# In-place Overwrite Templates in Java

This file contains common In-place Overwrite templates in Java.

Use these templates when the problem asks to modify the array directly without using another full array.

---

## Template 1: Keep Elements Based on Condition

Use when question asks:

```txt
Keep only valid elements.
Return new length.
```

Template:

```java
public int keepValidElements(int[] nums) {
    int index = 0;

    for (int i = 0; i < nums.length; i++) {
        if (condition) {
            nums[index] = nums[i];
            index++;
        }
    }

    return index;
}
```

Meaning:

```txt
i reads all elements.
index writes valid elements.
```

---

## Template 2: Remove Element

Use when question asks:

```txt
Remove all occurrences of val.
Return new length.
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

Example:

```txt
nums = [3, 2, 2, 3]
val = 3
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

## Template 3: Remove Duplicates from Sorted Array

Use when question asks:

```txt
Remove duplicates from sorted array.
Return number of unique elements.
```

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

Important:

```txt
Array must be sorted.
```

Why?

```txt
Because duplicate values stay together in sorted array.
```

---

## Template 4: Move Zeroes

Use when question asks:

```txt
Move all zeroes to end.
Keep order of non-zero elements.
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

Why two steps?

```txt
First keep non-zero elements.
Then fill remaining positions with zero.
```

---

## Template 5: Keep Positive Numbers

Use when question asks:

```txt
Move or keep positive numbers at front.
Return count of positives.
```

Code:

```java
public int keepPositive(int[] nums) {
    int index = 0;

    for (int i = 0; i < nums.length; i++) {
        if (nums[i] > 0) {
            nums[index] = nums[i];
            index++;
        }
    }

    return index;
}
```

---

## Template 6: Keep Even Numbers

Use when question asks:

```txt
Keep even numbers at front.
Return count of even numbers.
```

Code:

```java
public int keepEven(int[] nums) {
    int index = 0;

    for (int i = 0; i < nums.length; i++) {
        if (nums[i] % 2 == 0) {
            nums[index] = nums[i];
            index++;
        }
    }

    return index;
}
```

---

## Template 7: Remove Duplicates Allow At Most Twice

Use when question asks:

```txt
Sorted array.
Each value can appear at most twice.
Return new length.
```

Example:

```txt
nums = [1, 1, 1, 2, 2, 3]
```

Valid part:

```txt
[1, 1, 2, 2, 3]
```

Code:

```java
public int removeDuplicatesAllowTwice(int[] nums) {
    int index = 0;

    for (int i = 0; i < nums.length; i++) {
        if (index < 2 || nums[i] != nums[index - 2]) {
            nums[index] = nums[i];
            index++;
        }
    }

    return index;
}
```

Explanation:

```txt
index < 2 means first two elements are allowed.
nums[i] != nums[index - 2] prevents more than two copies.
```

---

## Template 8: Partition by Condition

Use when question asks:

```txt
Move elements satisfying condition to front.
Order may or may not matter depending on problem.
```

Stable version keeps order:

```java
public int partitionStable(int[] nums) {
    int index = 0;

    for (int i = 0; i < nums.length; i++) {
        if (condition) {
            nums[index] = nums[i];
            index++;
        }
    }

    return index;
}
```

Example conditions:

```txt
nums[i] != val
nums[i] > 0
nums[i] % 2 == 0
nums[i] != 0
```

---

## Template Selection Table

| Requirement | Template |
|---|---|
| Remove given value | Remove Element |
| Remove duplicates from sorted array | Remove Duplicates |
| Move zeroes to end | Move Zeroes |
| Keep positive numbers | Keep Positive |
| Keep even numbers | Keep Even |
| Allow at most two duplicates | Remove Duplicates Allow Twice |
| Keep values based on condition | General Keep Condition |

---

## How to Decide Which Template to Use?

Ask:

```txt
Which elements should stay?
```

| Question | Keep Condition |
|---|---|
| Remove Element | `nums[i] != val` |
| Move Zeroes | `nums[i] != 0` |
| Keep Even | `nums[i] % 2 == 0` |
| Keep Positive | `nums[i] > 0` |
| Remove Duplicates | `nums[i] != nums[i - 1]` |

---

## Beginner Rule

In-place Overwrite is mainly about one question:

```txt
Where should the next valid element be written?
```

That place is tracked by:

```java
index
```

So remember:

```txt
i reads
index writes
```
