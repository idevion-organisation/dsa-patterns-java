# Day 7 — Fast & Slow Pointer Pattern

> **Learning Goal**
>
> Learn one of the most important Linked List interview patterns used to efficiently find the middle node, detect cycles, and solve many advanced Linked List problems without using extra space.

---

# Why This Pattern?

Until now, we have learned how to:

- Create a Linked List
- Traverse a Linked List
- Search for a value
- Insert nodes
- Delete nodes
- Understand head and tail operations

But many interview problems require finding information about the list **without traversing it multiple times**.

Examples include:

- Finding the middle node
- Detecting if a cycle exists
- Finding the start of a cycle
- Checking if a Linked List is a palindrome
- Reordering a Linked List

Using normal traversal often requires multiple passes or extra memory.

The **Fast & Slow Pointer Pattern** solves these problems efficiently in **O(n) time** using **O(1) extra space**.

---

# What is the Fast & Slow Pointer Pattern?

Instead of using one pointer, we use **two pointers**:

- **Slow Pointer** → Moves one node at a time.
- **Fast Pointer** → Moves two nodes at a time.

```text
Slow → 1 step

A → B → C → D → E

Fast → 2 steps

A ==> C ==> E
```

Because the Fast pointer moves twice as quickly as the Slow pointer, they create useful relationships that help solve multiple Linked List problems.

---

# Intuition Behind the Pattern

Imagine two people running on a track.

- One person walks.
- One person runs twice as fast.

Eventually:

- The faster person reaches the end first.
- The slower person naturally reaches the halfway point.

Exactly the same idea is used inside a Linked List.

---

# Visual Example

Initial Position

```text
Head

10 → 20 → 30 → 40 → 50 → 60

S
F
```

Iteration 1

```text
10 → 20 → 30 → 40 → 50 → 60

     S
          F
```

Iteration 2

```text
10 → 20 → 30 → 40 → 50 → 60

          S
                    F
```

Iteration 3

```text
10 → 20 → 30 → 40 → 50 → 60

               S

Fast reaches NULL
```

Result:

Slow pointer automatically points to the middle node.

---

# Why Does This Work?

Suppose:

Fast moves **2 nodes**

Slow moves **1 node**

When Fast has travelled the complete Linked List,

Slow has travelled only half the distance.

Therefore,

**Slow reaches the middle automatically.**

No counting.

No extra variables.

No second traversal.

---

# Recognition Pattern

Whenever you see questions containing words like:

- Middle
- Half
- Midpoint
- Detect Loop
- Detect Cycle
- Find Meeting Point
- Reorder List
- Palindrome
- Split Linked List

Immediately think:

> **Fast & Slow Pointer Pattern**

---

# Where is this Pattern Used?

This is one of the highest-frequency interview patterns.

Examples include:

### Easy

- Middle of the Linked List

- Linked List Cycle

---

### Medium

- Linked List Cycle II

- Palindrome Linked List

- Reorder List

---

### Hard

- Split Circular Linked List

- Complex Linked List Rearrangement

- Advanced Cycle Problems

---

# Advantages

✅ Only one traversal

✅ Constant extra memory

✅ Very clean implementation

✅ Interview favorite

✅ Easy to combine with other patterns

---

# Time Complexity

Finding Middle

```text
Time  : O(n)

Space : O(1)
```

Cycle Detection

```text
Time  : O(n)

Space : O(1)
```

No extra HashMap.

No HashSet.

No Arrays.

---

# Common Mistakes

### ❌ Mistake 1

Moving both pointers one step.

Wrong

```java
slow = slow.next;
fast = fast.next;
```

Fast pointer must move **two steps**.

---

### ❌ Mistake 2

Forgetting NULL checks.

Wrong

```java
fast = fast.next.next;
```

Always check

```java
fast != null &&
fast.next != null
```

before moving.

---

### ❌ Mistake 3

Returning Fast pointer instead of Slow pointer.

Remember:

Fast finishes.

Slow gives the answer.

---

### ❌ Mistake 4

Thinking this pattern only finds the middle.

Actually, it also solves:

- Cycle Detection
- Cycle Entry
- Happy Number
- Palindrome
- Reorder List
- Split Linked List

---

# Interview Tip 💡

Whenever an interviewer asks:

- "Find the middle..."
- "Detect a cycle..."
- "Can you solve it without extra space?"

The expected solution is almost always based on the **Fast & Slow Pointer Pattern**.

Recognizing this signal quickly can save a lot of time during interviews.

---

# Key Takeaways

✔ Two pointers move at different speeds.

✔ Slow pointer reaches the middle automatically.

✔ Fast pointer helps detect cycles.

✔ Uses constant extra memory.

✔ One of the most important Linked List interview patterns.

✔ Foundation for many advanced Linked List questions.

---

# What's Next?

In the next lesson, we will learn another fundamental Linked List pattern:

> **Day 8 — Linked List Reversal Pattern**

This pattern is the backbone of many interview questions such as:

- Reverse Linked List
- Reverse Between Positions
- Reverse K Group
- Palindrome Linked List
- Reorder List

Understanding reversal will unlock many advanced Linked List problems.
