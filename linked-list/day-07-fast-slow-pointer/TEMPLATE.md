# Fast & Slow Pointer Pattern — Java Templates

> **Goal**
>
> This file contains reusable Java templates for solving Linked List problems using the **Fast & Slow Pointer Pattern**.
>
> Learn the pattern first, then adapt the template according to the problem statement.

---

# Pattern Overview

Instead of using a single pointer, maintain two pointers.

- **Slow Pointer** → Moves one node at a time.
- **Fast Pointer** → Moves two nodes at a time.

```text
Head

10 → 20 → 30 → 40 → 50 → 60

Slow : 1 step

Fast : 2 steps
```

Whenever a problem asks for:

- Middle node
- Cycle detection
- Cycle entry
- Palindrome
- Reorder List

Think about the **Fast & Slow Pointer Pattern**.

---

# Template 1 — Find Middle Node

### Use When

- Find the middle node.
- Split Linked List.
- Find midpoint.

### Java Template

```java
ListNode slow = head;
ListNode fast = head;

while (fast != null && fast.next != null) {

    slow = slow.next;
    fast = fast.next.next;

}

return slow;
```

---

### Dry Run

Input

```text
1 → 2 → 3 → 4 → 5
```

|Iteration|Slow|Fast|
|---------|----|----|
|1|2|3|
|2|3|5|

Fast reaches the end.

Answer:

```text
3
```

---

Time Complexity

```text
O(n)
```

Space Complexity

```text
O(1)
```

---

# Template 2 — Detect Cycle

### Use When

The question asks:

- Does a cycle exist?
- Detect loop.
- Return true or false.

### Java Template

```java
ListNode slow = head;
ListNode fast = head;

while (fast != null && fast.next != null) {

    slow = slow.next;
    fast = fast.next.next;

    if (slow == fast) {
        return true;
    }

}

return false;
```

---

### Dry Run

```text
1 → 2 → 3 → 4
     ↑       ↓
     ← ← ← ←
```

Eventually,

Fast catches Slow.

Cycle detected.

---

Time Complexity

```text
O(n)
```

Space Complexity

```text
O(1)
```

---

# Template 3 — Find Starting Node of Cycle

### Use When

The problem asks:

- Return cycle starting node.
- Find where the loop begins.

### Java Template

```java
ListNode slow = head;
ListNode fast = head;

while (fast != null && fast.next != null) {

    slow = slow.next;
    fast = fast.next.next;

    if (slow == fast) {

        ListNode entry = head;

        while (entry != slow) {
            entry = entry.next;
            slow = slow.next;
        }

        return entry;
    }

}

return null;
```

---

### Dry Run

```text
1 → 2 → 3 → 4 → 5
         ↑       ↓
         ← ← ← ←
```

After first meeting,

Move one pointer back to Head.

Move both pointers one step at a time.

They meet exactly at the cycle entry.

---

Time Complexity

```text
O(n)
```

Space Complexity

```text
O(1)
```

---

# Template 4 — Find First Half and Second Half

This template is frequently used before:

- Reverse Linked List
- Palindrome Linked List
- Reorder List
- Merge Problems

```java
ListNode slow = head;
ListNode fast = head;

while (fast != null && fast.next != null) {

    slow = slow.next;
    fast = fast.next.next;

}

// slow points to middle
```

After this,

```text
Head

↓

1 → 2 → 3 → 4 → 5

        ↑

      slow
```

The second half starts from:

```java
slow.next
```

or

```java
slow
```

depending on the problem.

---

# Recognition Checklist

Before writing code, ask yourself:

✅ Do I need the middle node?

✅ Do I need to detect a loop?

✅ Do I need to split the Linked List?

✅ Do I need constant extra space?

✅ Can two pointers moving at different speeds solve it?

If the answer is **YES**, use the **Fast & Slow Pointer Pattern**.

---

# Common Mistakes

### ❌ Mistake 1

```java
fast = fast.next;
```

Correct

```java
fast = fast.next.next;
```

---

### ❌ Mistake 2

Skipping null checks.

Wrong

```java
fast.next.next
```

Correct

```java
while (fast != null && fast.next != null)
```

---

### ❌ Mistake 3

Returning Fast instead of Slow.

Remember

```text
Fast finishes.

Slow gives the answer.
```

---

### ❌ Mistake 4

Using extra arrays or HashMaps.

This pattern is specifically designed to solve these problems in **O(1)** extra space.

---

# Interview Tips

💡 The interviewer may not explicitly say **Fast & Slow Pointer**.

Instead, look for keywords like:

- Middle
- Midpoint
- Cycle
- Loop
- Reorder
- Palindrome
- Half of Linked List

These are strong signals that this pattern is expected.

---

# Summary

| Pattern | Purpose |
|---------|---------|
| Fast & Slow Pointer | Find middle node |
| Fast & Slow Pointer | Detect cycle |
| Fast & Slow Pointer | Find cycle entry |
| Fast & Slow Pointer | Split Linked List |
| Fast & Slow Pointer | Foundation for Palindrome & Reorder problems |

---

## Next Step

Before solving interview questions,

make sure you can:

✅ Write all three templates from memory.

✅ Explain **why** Fast moves two steps.

✅ Explain **why** Slow reaches the middle.

Once you are comfortable with these templates,

move to **PRACTICE.md** and solve the curated problems.
