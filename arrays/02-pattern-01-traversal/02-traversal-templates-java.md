# Traversal Templates in Java

These are common Java templates used in traversal-based array problems.

---

## Template 1: Print All Elements

```java
for (int i = 0; i < arr.length; i++) {
    System.out.println(arr[i]);
}
```

Use when:

```txt
You need to visit every element.
```

---

## Template 2: Sum of Array

```java
int sum = 0;

for (int i = 0; i < arr.length; i++) {
    sum += arr[i];
}
```

Use when:

```txt
Question asks for total or sum.
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

## Template 3: Maximum Element

```java
int max = arr[0];

for (int i = 1; i < arr.length; i++) {
    if (arr[i] > max) {
        max = arr[i];
    }
}
```

Use when:

```txt
Question asks for largest element.
```

Important:

```txt
Start max with arr[0], not 0.
```

---

## Template 4: Minimum Element

```java
int min = arr[0];

for (int i = 1; i < arr.length; i++) {
    if (arr[i] < min) {
        min = arr[i];
    }
}
```

Use when:

```txt
Question asks for smallest element.
```

---

## Template 5: Count Elements Based on Condition

```java
int count = 0;

for (int i = 0; i < arr.length; i++) {
    if (arr[i] % 2 == 0) {
        count++;
    }
}
```

Use when:

```txt
Question asks how many elements satisfy a condition.
```

Examples:

```txt
count even numbers
count odd numbers
count positive numbers
count negative numbers
count numbers greater than x
```

---

## Template 6: Average of Array

```java
int sum = 0;

for (int i = 0; i < arr.length; i++) {
    sum += arr[i];
}

double average = (double) sum / arr.length;
```

Use when:

```txt
Question asks for average.
```

Important:

```java
(double) sum
```

This avoids integer division.

---

## Template 7: Enhanced For Loop

```java
for (int num : arr) {
    System.out.println(num);
}
```

Use when:

```txt
Only value is needed.
```

Do not use enhanced loop when index is required.

---

## Normal Loop vs Enhanced Loop

| Loop | Use When |
|---|---|
| Normal `for` loop | Need index |
| Enhanced `for` loop | Only need value |

---

## Template 8: 2D Array Traversal

```java
for (int i = 0; i < matrix.length; i++) {
    for (int j = 0; j < matrix[0].length; j++) {
        System.out.print(matrix[i][j] + " ");
    }
    System.out.println();
}
```

Use when:

```txt
Question has matrix or grid.
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

## Quick Template Selection

| Problem Type | Template |
|---|---|
| Print elements | Print all elements |
| Find sum | Sum template |
| Find max | Maximum template |
| Find min | Minimum template |
| Count condition | Count template |
| Find average | Average template |
| Matrix traversal | 2D traversal |

---

## Beginner Checklist

Before using traversal, ask:

```txt
Do I need to check every element?
Do I need index?
Do I need value only?
Do I need to update answer variable?
What is the condition?
```
