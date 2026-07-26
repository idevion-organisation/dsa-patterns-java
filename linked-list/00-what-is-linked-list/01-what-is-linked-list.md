# What is Linked List?

A **linked list** is a linear data structure where data is stored in the form of connected nodes.

Unlike arrays, linked list elements are not stored in continuous memory.

Instead, each element is stored inside a node, and every node points to the next node.

---

## Why This Topic Matters

Linked List is one of the most important DSA topics because it builds the foundation for:

```txt
pointer movement
reference handling
node connection
head changes
null handling
insertion and deletion logic
reversal problems
cycle detection
fast and slow pointer problems
```

Many students find linked list difficult because they try to memorize code.

But linked list becomes easier when you understand how nodes are connected and how pointers move.

---

## Simple Definition

A linked list is a chain of nodes.

Each node contains:

```txt
value
reference to the next node
```

Example:

```txt
10 → 20 → 30 → null
```

This means:

```txt
10 points to 20
20 points to 30
30 points to null
null means the list ends
```

---

## Basic Node Structure

A linked list node has two parts:

```txt
data/value
next reference
```

Visual form:

```txt
+-------+------+
| value | next |
+-------+------+
```

Example node:

```txt
+----+------+
| 10 | next |
+----+------+
```

If this node points to another node containing `20`, then:

```txt
+----+------+     +----+------+
| 10 | next | --> | 20 | next |
+----+------+     +----+------+
```

---

## Linked List Example

```txt
head
 |
 v
10 → 20 → 30 → null
```

Here:

| Part | Meaning |
|---|---|
| `head` | Reference to the first node |
| `10` | First node value |
| `20` | Second node value |
| `30` | Last node value |
| `null` | End of linked list |

---

## Important Terms

| Term | Meaning |
|---|---|
| Node | Single unit of a linked list |
| Value / Data | Actual data stored in the node |
| Next | Reference to the next node |
| Head | First node of the linked list |
| Tail | Last node of the linked list |
| null | Indicates that no next node exists |
| Reference | Address-like link to another node |

---

## Java Node Class

In Java, a linked list node is usually represented using a class.

```java
class ListNode {
    int val;
    ListNode next;

    ListNode(int val) {
        this.val = val;
        this.next = null;
    }
}
```

---

## Explanation of Node Class

```txt
class ListNode
```

Creates a node structure.

```txt
int val
```

Stores the value of the node.

```txt
ListNode next
```

Stores the reference of the next node.

```txt
this.val = val
```

Assigns the given value to the node.

```txt
this.next = null
```

By default, the new node does not point to any other node.

---

## Creating a Linked List Manually

To create this linked list:

```txt
10 → 20 → 30 → null
```

Java code:

```java
class Main {
    public static void main(String[] args) {
        ListNode first = new ListNode(10);
        ListNode second = new ListNode(20);
        ListNode third = new ListNode(30);

        first.next = second;
        second.next = third;
        third.next = null;

        ListNode head = first;
    }
}
```

---

## Step-by-Step Connection

Initially:

```txt
first  = 10 → null
second = 20 → null
third  = 30 → null
```

After:

```java
first.next = second;
```

Structure becomes:

```txt
10 → 20 → null
30 → null
```

After:

```java
second.next = third;
```

Structure becomes:

```txt
10 → 20 → 30 → null
```

After:

```java
ListNode head = first;
```

Now `head` points to the first node:

```txt
head → 10 → 20 → 30 → null
```

---

## What is Head?

The `head` is the starting point of a linked list.

```java
ListNode head = first;
```

Without the head, we cannot access the full linked list.

If the head is lost, the list becomes unreachable.

---

## Empty Linked List

If:

```java
ListNode head = null;
```

Then the linked list is empty.

Visual:

```txt
head → null
```

This means:

```txt
there is no node in the list
```

---

## Single Node Linked List

Example:

```txt
head → 10 → null
```

This linked list has only one node.

Here:

```txt
head points to 10
10 points to null
```

The first node is also the last node.

---

## Linked List vs Array

| Point | Array | Linked List |
|---|---|---|
| Memory | Continuous | Non-continuous |
| Access | Direct using index | Node by node |
| Size | Fixed or resizing needed | Dynamic |
| Insert at beginning | Costly | Easier |
| Delete at beginning | Costly | Easier |
| Extra memory | No pointer/reference needed | Extra next reference needed |
| Traversal | Index based | Reference based |
| Cache performance | Better | Usually weaker |

---

## Why Linked List Does Not Have Direct Indexing

In an array:

```java
arr[2]
```

can directly access the third element.

But in a linked list, there is no direct index jump.

To reach the third node, we must start from `head` and move one node at a time.

Example:

```txt
head → 10 → 20 → 30 → null
```

To reach `30`, we move:

```txt
10 → 20 → 30
```

That is why linked list access is slower than array access.

---

## Basic Traversal

Traversal means visiting each node one by one.

```java
ListNode current = head;

while (current != null) {
    System.out.println(current.val);
    current = current.next;
}
```

---

## Why Use `current`?

We use a temporary pointer:

```java
ListNode current = head;
```

because we do not want to lose the original `head`.

Correct:

```java
ListNode current = head;

while (current != null) {
    current = current.next;
}
```

Risky:

```java
while (head != null) {
    head = head.next;
}
```

This moves the actual head reference and can lose access to the original list.

---

## Traversal Dry Run

Linked list:

```txt
head → 10 → 20 → 30 → null
```

Code:

```java
ListNode current = head;

while (current != null) {
    System.out.println(current.val);
    current = current.next;
}
```

Dry run:

| Step | current points to | Printed value | After `current = current.next` |
|---:|---|---:|---|
| 1 | 10 | 10 | 20 |
| 2 | 20 | 20 | 30 |
| 3 | 30 | 30 | null |
| 4 | null | loop stops | end |

Output:

```txt
10
20
30
```

---

## Why Check `current != null`?

We write:

```java
while (current != null)
```

because `null` means there is no node left.

If we try:

```java
current.val
```

when `current` is `null`, Java throws:

```txt
NullPointerException
```

---

## Memory Thinking

In arrays, elements are placed side by side.

```txt
Array:
[10][20][30]
```

In linked list, nodes can be anywhere in memory.

```txt
Linked List:
10 → 20 → 30 → null
```

The connection is maintained using references.

This is why linked list is based on links, not indexes.

---

## Types of Linked List

For now, we focus on **singly linked list**.

### 1. Singly Linked List

Each node points only to the next node.

```txt
10 → 20 → 30 → null
```

### 2. Doubly Linked List

Each node points to both previous and next nodes.

```txt
null ← 10 ⇄ 20 ⇄ 30 → null
```

### 3. Circular Linked List

The last node points back to the first node.

```txt
10 → 20 → 30
↑         ↓
└─────────┘
```

In this module, we mainly use singly linked list because most beginner and interview linked list problems are based on it.

---

## Linked List Problem Thinking

When solving linked list problems, always track:

```txt
head
current
previous
next
slow
fast
dummy
```

Different patterns use different pointers.

For example:

| Pointer | Used For |
|---|---|
| `current` | Traversal |
| `previous` | Reversal and deletion |
| `next` | Saving next node before changing links |
| `slow` | Middle and cycle problems |
| `fast` | Fast-slow pointer pattern |
| `dummy` | Handling head edge cases |

---

## How to Recognize Linked List Problems

A problem is usually a linked list problem if it says:

```txt
given the head of a linked list
return the modified list
delete a node
reverse a list
detect a cycle
find middle node
merge two lists
remove nth node from end
```

Common input style:

```java
public ListNode solve(ListNode head) {
    
}
```

or:

```java
public ListNode solve(ListNode head1, ListNode head2) {
    
}
```

---

## Most Important Beginner Rule

Never change links blindly.

Before changing:

```java
current.next = something;
```

always ask:

```txt
Will I lose access to the next node?
Do I need to store next first?
Can head change?
What happens if the list is empty?
What happens if there is only one node?
```

---

## Common Beginner Mistakes

| Mistake | Why it is wrong | Correct thinking |
|---|---|---|
| Moving `head` directly | Original list start can be lost | Use `current` |
| Forgetting null check | Causes NullPointerException | Check `current != null` |
| Confusing value and reference | Value is data, reference connects nodes | Track both separately |
| Changing `next` too early | Can lose remaining list | Store next before rewiring |
| Ignoring empty list | Code may fail on `head == null` | Handle edge cases |
| Ignoring single node list | Many pointer operations fail | Test one-node case |

---

## Day 1 Pattern Signal

Day 1 is foundation, not a pattern yet.

But the signal is:

```txt
You need to understand node movement before solving linked list patterns.
```

If a problem involves moving from one node to another, linked list traversal is the first skill required.

---

## Day 1 Learning Goal

After completing Day 1, you should be able to explain:

```txt
what a linked list is
what a node is
what head means
what next means
why null means the end
how nodes are connected
how traversal works
why linked list has no direct indexing
how linked list differs from array
why null checks are important
why moving head directly can be risky
```

---

## Final Revision

```txt
Linked List = connected nodes
Node = value + next reference
Head = first node
Next = reference to next node
Null = end of list
Traversal = moving node by node
Index access = not directly possible
Main skill = pointer/reference handling
```

---

## Final Checklist

| Concept | Status |
|---|---|
| Understand linked list meaning | ✅ |
| Understand node structure | ✅ |
| Understand head pointer | ✅ |
| Understand next reference | ✅ |
| Understand null ending | ✅ |
| Understand empty list | ✅ |
| Understand single node list | ✅ |
| Understand traversal | ✅ |
| Understand array vs linked list difference | ✅ |
| Understand Java ListNode class | ✅ |
| Understand beginner mistakes | ✅ |
