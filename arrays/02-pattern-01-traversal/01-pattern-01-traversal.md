# Pattern 01: Traversal

Traversal is the most basic and most important array pattern.

Traversal means visiting each element of the array one by one.

```txt
Start from index 0
Visit each element
Stop at last index
```

---

## When to Use Traversal?

Use traversal when the problem asks you to:

```txt
print elements
find sum
find maximum
find minimum
count elements
check conditions
calculate average
process every element
```

If every element needs to be checked, traversal is usually the first pattern.

---

## Pattern Signal

If the question contains words like:

```txt
sum
count
maximum
minimum
average
total
number of elements
how many
```

Think:

```txt
Traversal
```

---

## Basic Idea

For an array:

```java
int[] arr = {10, 20, 30, 40};
```

Traversal means:

```txt
arr[0] → arr[1] → arr[2] → arr[3]
```

---

## Basic Java Code

```java
for (int i = 0; i < arr.length; i++) {
    System.out.println(arr[i]);
}
```

Here:

```txt
i = index
arr[i] = value at that index
```

---

## Dry Run

```java
int[] arr = {5, 10, 15};
```

| Step | `i` | `arr[i]` | Output |
|---:|---:|---:|---:|
| 1 | 0 | 5 | 5 |
| 2 | 1 | 10 | 10 |
| 3 | 2 | 15 | 15 |

Loop stops when:

```txt
i = 3
3 < arr.length
3 < 3 → false
```

---

## Example 1: Sum of Array

```java
int[] arr = {1, 2, 3, 4};
int sum = 0;

for (int i = 0; i < arr.length; i++) {
    sum += arr[i];
}

System.out.println(sum);
```

Output:

```txt
10
```

### Dry Run

| Step | Element | Sum |
|---:|---:|---:|
| 1 | 1 | 1 |
| 2 | 2 | 3 |
| 3 | 3 | 6 |
| 4 | 4 | 10 |

---

## Example 2: Maximum Element

```java
int[] arr = {5, 9, 2, 11};
int max = arr[0];

for (int i = 1; i < arr.length; i++) {
    if (arr[i] > max) {
        max = arr[i];
    }
}

System.out.println(max);
```

Output:

```txt
11
```

Important:

```java
int max = arr[0];
```

Do not start with `0`, because the array may contain negative numbers.

---

## Example 3: Count Even Numbers

```java
int[] arr = {2, 5, 8, 9, 10};
int count = 0;

for (int i = 0; i < arr.length; i++) {
    if (arr[i] % 2 == 0) {
        count++;
    }
}

System.out.println(count);
```

Output:

```txt
3
```

---

## Time and Space Complexity

| Operation | Complexity |
|---|---:|
| Time Complexity | O(n) |
| Space Complexity | O(1) |

Why time is O(n)?

```txt
Because we visit every element once.
```

Why space is O(1)?

```txt
Because we use only a few extra variables.
```

---

## Common Mistakes

### 1. Using `<= arr.length`

Wrong:

```java
for (int i = 0; i <= arr.length; i++)
```

Correct:

```java
for (int i = 0; i < arr.length; i++)
```

---

### 2. Starting max with 0

Wrong:

```java
int max = 0;
```

Correct:

```java
int max = arr[0];
```

This matters when array has negative values.

---

### 3. Forgetting to update answer

Wrong:

```java
if (arr[i] > max) {
    arr[i] = max;
}
```

Correct:

```java
if (arr[i] > max) {
    max = arr[i];
}
```

---

## Pattern Summary

| Point | Meaning |
|---|---|
| Pattern Name | Traversal |
| Used For | Sum, count, max, min, condition checking |
| Main Logic | Visit every element |
| Time | O(n) |
| Space | O(1) |
| Common Loop | `for (int i = 0; i < arr.length; i++)` |

---

## Next Pattern

```txt
Pattern 02: Linear Search
```
