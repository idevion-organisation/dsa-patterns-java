# Rotate, Dutch Flag, Product Except Self, Difference Array Templates in Java

This file contains reusable Java templates for advanced array manipulation patterns.

Covered templates:

```txt
1. Rotate Array
2. Dutch National Flag
3. Product Except Self
4. Difference Array
```

---

# Template 1: Rotate Array Right by K

Use when question asks:

```txt
Rotate array to the right by k steps.
```

Code:

```java
public void rotateRight(int[] nums, int k) {
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

---

# Template 2: Rotate Array Left by K

Use when question asks:

```txt
Rotate array to the left by k steps.
```

Example:

```txt
nums = [1, 2, 3, 4, 5]
k = 2
```

Output:

```txt
[3, 4, 5, 1, 2]
```

Code:

```java
public void rotateLeft(int[] nums, int k) {
    int n = nums.length;

    k = k % n;

    reverse(nums, 0, k - 1);
    reverse(nums, k, n - 1);
    reverse(nums, 0, n - 1);
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

---

# Template 3: Rotate Right Using Extra Array

Use when beginner wants a simple approach.

Code:

```java
public int[] rotateRightExtraArray(int[] nums, int k) {
    int n = nums.length;
    int[] result = new int[n];

    k = k % n;

    for (int i = 0; i < n; i++) {
        int newIndex = (i + k) % n;
        result[newIndex] = nums[i];
    }

    return result;
}
```

Formula:

```txt
newIndex = (i + k) % n
```

Space:

```txt
O(n)
```

---

# Template 4: Sort Colors / Dutch National Flag

Use when question asks:

```txt
Sort array containing only 0, 1, and 2.
```

Code:

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

---

# Template 5: Partition 0s and 1s

Use when array contains only:

```txt
0 and 1
```

Code:

```java
public void sortZeroOne(int[] nums) {
    int left = 0;
    int right = nums.length - 1;

    while (left < right) {
        while (left < right && nums[left] == 0) {
            left++;
        }

        while (left < right && nums[right] == 1) {
            right--;
        }

        if (left < right) {
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

# Template 6: Product Except Self

Use when question asks:

```txt
Return product of array except current index.
Do not use division.
```

Code:

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

Time:

```txt
O(n)
```

Space:

```txt
O(1) extra excluding output array
```

---

# Template 7: Product Except Self With Prefix and Suffix Arrays

Use when beginner wants easier understanding.

Code:

```java
public int[] productExceptSelfEasy(int[] nums) {
    int n = nums.length;

    int[] prefix = new int[n];
    int[] suffix = new int[n];
    int[] answer = new int[n];

    prefix[0] = 1;

    for (int i = 1; i < n; i++) {
        prefix[i] = prefix[i - 1] * nums[i - 1];
    }

    suffix[n - 1] = 1;

    for (int i = n - 2; i >= 0; i--) {
        suffix[i] = suffix[i + 1] * nums[i + 1];
    }

    for (int i = 0; i < n; i++) {
        answer[i] = prefix[i] * suffix[i];
    }

    return answer;
}
```

This version is easier to understand but uses more space.

---

# Template 8: Build Difference Array From Original Array

Use when question gives original array and asks for range updates.

Code:

```java
public int[] buildDifferenceArray(int[] nums) {
    int n = nums.length;
    int[] diff = new int[n];

    diff[0] = nums[0];

    for (int i = 1; i < n; i++) {
        diff[i] = nums[i] - nums[i - 1];
    }

    return diff;
}
```

---

# Template 9: Apply One Range Update on Difference Array

Use when question asks:

```txt
Add value to range [left, right].
```

Code:

```java
public void applyUpdate(int[] diff, int left, int right, int value) {
    diff[left] += value;

    if (right + 1 < diff.length) {
        diff[right + 1] -= value;
    }
}
```

---

# Template 10: Reconstruct Array From Difference Array

Use after applying all range updates.

Code:

```java
public int[] reconstructArray(int[] diff) {
    int n = diff.length;
    int[] result = new int[n];

    result[0] = diff[0];

    for (int i = 1; i < n; i++) {
        result[i] = result[i - 1] + diff[i];
    }

    return result;
}
```

---

# Template 11: Range Update From Empty Array

Use when question gives:

```txt
length n
updates = [left, right, value]
```

Code:

```java
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
```

---

# Template Selection Table

| Requirement | Template |
|---|---|
| Rotate right by k | Reverse method |
| Rotate left by k | Reverse method |
| Simple rotate with extra space | Extra array rotation |
| Sort 0s, 1s, 2s | Dutch National Flag |
| Sort 0s and 1s | Two-pointer partition |
| Product except self | Prefix + suffix product |
| Product except self easy | Prefix array + suffix array |
| Range update | Difference array |
| Rebuild after updates | Prefix reconstruction |

---

# How to Decide Which Template to Use?

Ask:

```txt
What type of array transformation is needed?
```

| Question Says | Use |
|---|---|
| rotate by k | Rotate Array |
| sort colors / 0,1,2 | Dutch National Flag |
| product except current | Product Except Self |
| add value to many ranges | Difference Array |
| range update queries | Difference Array |
| without division | Prefix + suffix product |
| in-place rotation | Reverse method |

---

# Beginner Rule

Remember these four main ideas:

```txt
Rotate Array:
Reverse full array and then reverse parts.

Dutch Flag:
Use low, mid, high.

Product Except Self:
Left product × right product.

Difference Array:
Start effect at left, stop effect after right.
```
