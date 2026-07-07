# Linear Search Templates in Java

This file contains common Linear Search templates in Java.

Use these templates when the problem asks you to search, find, check, count, or locate an element in an array.

---

## Template 1: Return Index of Target

Use when question asks:

```txt
Return index of target.
Return -1 if target is not found.
```

Code:

```java
public int search(int[] nums, int target) {
    for (int i = 0; i < nums.length; i++) {
        if (nums[i] == target) {
            return i;
        }
    }

    return -1;
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

## Template 2: Return True or False

Use when question asks:

```txt
Check whether target exists or not.
```

Code:

```java
public boolean containsTarget(int[] nums, int target) {
    for (int i = 0; i < nums.length; i++) {
        if (nums[i] == target) {
            return true;
        }
    }

    return false;
}
```

Return:

```txt
true  → target exists
false → target does not exist
```

---

## Template 3: Return First Occurrence

Use when question asks:

```txt
Find first index of target.
```

Code:

```java
public int firstOccurrence(int[] nums, int target) {
    for (int i = 0; i < nums.length; i++) {
        if (nums[i] == target) {
            return i;
        }
    }

    return -1;
}
```

Why it works:

```txt
Because loop starts from left side.
First match is the first occurrence.
```

---

## Template 4: Return Last Occurrence

Use when question asks:

```txt
Find last index of target.
```

Code:

```java
public int lastOccurrence(int[] nums, int target) {
    int ans = -1;

    for (int i = 0; i < nums.length; i++) {
        if (nums[i] == target) {
            ans = i;
        }
    }

    return ans;
}
```

Why it works:

```txt
We keep updating ans whenever target is found.
The final ans becomes last occurrence.
```

Alternative from right to left:

```java
public int lastOccurrence(int[] nums, int target) {
    for (int i = nums.length - 1; i >= 0; i--) {
        if (nums[i] == target) {
            return i;
        }
    }

    return -1;
}
```

---

## Template 5: Count Occurrences

Use when question asks:

```txt
Count how many times target appears.
```

Code:

```java
public int countOccurrence(int[] nums, int target) {
    int count = 0;

    for (int i = 0; i < nums.length; i++) {
        if (nums[i] == target) {
            count++;
        }
    }

    return count;
}
```

Important:

```txt
Do not return immediately.
You must check the full array.
```

---

## Template 6: Return All Indexes

Use when question asks:

```txt
Return all indexes where target appears.
```

Code:

```java
import java.util.ArrayList;
import java.util.List;

public List<Integer> allIndexes(int[] nums, int target) {
    List<Integer> indexes = new ArrayList<>();

    for (int i = 0; i < nums.length; i++) {
        if (nums[i] == target) {
            indexes.add(i);
        }
    }

    return indexes;
}
```

Example:

```txt
nums = [2, 5, 2, 7, 2]
target = 2
```

Output:

```txt
[0, 2, 4]
```

Space:

```txt
O(k)
```

where `k` is the number of target occurrences.

---

## Template 7: Search in 2D Array

Use when question has:

```txt
matrix
grid
2D array
```

Code:

```java
public boolean search2D(int[][] matrix, int target) {
    for (int i = 0; i < matrix.length; i++) {
        for (int j = 0; j < matrix[0].length; j++) {
            if (matrix[i][j] == target) {
                return true;
            }
        }
    }

    return false;
}
```

Time:

```txt
O(rows × columns)
```

Space:

```txt
O(1)
```

---

## Template 8: Search and Return Position in 2D Array

Use when question asks:

```txt
Return row and column of target.
```

Code:

```java
public int[] search2DPosition(int[][] matrix, int target) {
    for (int i = 0; i < matrix.length; i++) {
        for (int j = 0; j < matrix[0].length; j++) {
            if (matrix[i][j] == target) {
                return new int[]{i, j};
            }
        }
    }

    return new int[]{-1, -1};
}
```

Example:

```txt
matrix = [
  [1, 2, 3],
  [4, 5, 6]
]

target = 5
```

Output:

```txt
[1, 1]
```

---

## Template Selection Table

| Requirement | Template |
|---|---|
| Return index | Index template |
| Return true/false | Boolean template |
| Find first index | First occurrence |
| Find last index | Last occurrence |
| Count target | Count occurrence |
| Return all target indexes | All indexes |
| Search in matrix | 2D search |
| Return matrix position | 2D position |

---

## How to Decide Which Template to Use?

Ask:

```txt
What does the question want?
```

| Question Wants | Return Type |
|---|---|
| Index | `int` |
| Exists or not | `boolean` |
| Count | `int` |
| All indexes | `List<Integer>` |
| 2D position | `int[]` |

---

## Beginner Rule

Linear Search is not about memorizing code.

It is about knowing:

```txt
What am I searching for?
What should I return?
Should I stop early or continue?
```

If the answer is clear, the code becomes simple.
