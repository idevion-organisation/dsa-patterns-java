# Linked List Complexity

This file explains the time and space complexity of basic linked list operations.

Complexity is important in linked list because linked list does not provide direct index-based access like arrays.

In most linked list operations, we start from the head and move node by node.

---

## Why Complexity Matters

Many beginners assume linked list operations are always faster than arrays.

That is not true.

Linked list is better in some operations, but weaker in others.

The main reason is:

```txt
Linked List does not support direct indexing.
```

So before solving any problem, ask:

```txt
Do I need to search?
Do I need to traverse?
Do I need to insert/delete?
Do I already have the node?
Can head change?
```

---

## Basic Complexity Summary

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| Access by index | O(n) | O(1) |
| Search by value | O(n) | O(1) |
| Traverse full list | O(n) | O(1) |
| Find length | O(n) | O(1) |
| Insert at head | O(1) | O(1) |
| Insert after a given node | O(1) | O(1) |
| Insert at tail without tail pointer | O(n) | O(1) |
| Insert at tail with tail pointer | O(1) | O(1) |
| Delete head | O(1) | O(1) |
| Delete after a given node | O(1) | O(1) |
| Delete by value | O(n) | O(1) |
| Reverse linked list | O(n) | O(1) |
| Detect cycle | O(n) | O(1) |

---

## Access by Index

In an array:

```java
arr[3]
```

accesses the fourth element directly.

Time complexity:

```txt
O(1)
```

In linked list, we cannot jump directly to index `3`.

Example:

```txt
head → 10 → 20 → 30 → 40 → null
```

To access `40`, we visit:

```txt
10
20
30
40
```

Time complexity:

```txt
O(n)
```

---

## Search by Value

To search for a value, we may need to check every node.

Example:

```txt
head → 10 → 20 → 30 → 40 → null
```

Search target:

```txt
40
```

Dry run:

| Step | Current node | Is target found? |
|---:|---:|---|
| 1 | 10 | No |
| 2 | 20 | No |
| 3 | 30 | No |
| 4 | 40 | Yes |

Worst case:

```txt
target is at the end
target does not exist
```

Time complexity:

```txt
O(n)
```

Space complexity:

```txt
O(1)
```

---

## Traversal

Traversal means visiting every node once.

```java
ListNode current = head;

while (current != null) {
    current = current.next;
}
```

If the list has `n` nodes, we visit `n` nodes.

Time complexity:

```txt
O(n)
```

Space complexity:

```txt
O(1)
```

because only one extra pointer is used.

---

## Find Length

To find the length, count nodes one by one.

```java
class Solution {
    public int findLength(ListNode head) {
        int length = 0;
        ListNode current = head;

        while (current != null) {
            length++;
            current = current.next;
        }

        return length;
    }
}
```

Time complexity:

```txt
O(n)
```

Space complexity:

```txt
O(1)
```

---

## Insert at Head

Before:

```txt
head → 10 → 20 → 30 → null
```

Insert `5` at head.

Steps:

```java
newNode.next = head;
head = newNode;
```

After:

```txt
head → 5 → 10 → 20 → 30 → null
```

Only two pointer changes are needed.

Time complexity:

```txt
O(1)
```

Space complexity:

```txt
O(1)
```

---

## Insert After a Given Node

Given:

```txt
10 → 20 → 30 → null
```

Insert `25` after `20`.

Steps:

```java
newNode.next = current.next;
current.next = newNode;
```

After:

```txt
10 → 20 → 25 → 30 → null
```

If the node `20` is already given, insertion is:

```txt
O(1)
```

But if we first need to search for `20`, total time becomes:

```txt
O(n)
```

Important:

```txt
Finding the position costs O(n)
Actual insertion costs O(1)
```

---

## Insert at Tail Without Tail Pointer

Given:

```txt
head → 10 → 20 → 30 → null
```

To insert `40` at the end, we first reach the last node.

Steps:

```txt
current = 10
current = 20
current = 30
insert after 30
```

Time complexity:

```txt
O(n)
```

because we traverse to the end.

---

## Insert at Tail With Tail Pointer

If we maintain a `tail` pointer:

```txt
head → 10 → 20 → 30 ← tail
```

Insert `40`:

```java
tail.next = newNode;
tail = newNode;
```

After:

```txt
head → 10 → 20 → 30 → 40 ← tail
```

Time complexity:

```txt
O(1)
```

---

## Delete Head

Before:

```txt
head → 10 → 20 → 30 → null
```

Delete head:

```java
head = head.next;
```

After:

```txt
head → 20 → 30 → null
```

Time complexity:

```txt
O(1)
```

---

## Delete After a Given Node

Given:

```txt
10 → 20 → 30 → 40 → null
```

If we are given node `20`, and we want to delete node `30`:

```java
current.next = current.next.next;
```

After:

```txt
10 → 20 → 40 → null
```

Time complexity:

```txt
O(1)
```

because the previous node is already known.

---

## Delete by Value

Given:

```txt
10 → 20 → 30 → 40 → null
```

Delete:

```txt
30
```

We need to find node `30` and its previous node `20`.

Then:

```java
previous.next = current.next;
```

After:

```txt
10 → 20 → 40 → null
```

Time complexity:

```txt
O(n)
```

because search is required.

---

## Reverse Linked List Complexity

To reverse:

```txt
10 → 20 → 30 → null
```

into:

```txt
30 → 20 → 10 → null
```

we must visit every node once.

Time complexity:

```txt
O(n)
```

Iterative space complexity:

```txt
O(1)
```

Recursive space complexity:

```txt
O(n)
```

because recursion uses call stack.

---

## Cycle Detection Complexity

Cycle detection using fast and slow pointers:

```txt
slow moves 1 step
fast moves 2 steps
```

Time complexity:

```txt
O(n)
```

Space complexity:

```txt
O(1)
```

because no extra data structure is needed.

---

## Array vs Linked List Complexity

| Operation | Array | Linked List |
|---|---:|---:|
| Access by index | O(1) | O(n) |
| Search by value | O(n) | O(n) |
| Insert at beginning | O(n) | O(1) |
| Delete at beginning | O(n) | O(1) |
| Insert after known position | O(n) if shifting needed | O(1) if node known |
| Delete after known position | O(n) if shifting needed | O(1) if previous node known |
| Memory locality | Better | Weaker |
| Extra reference memory | No | Yes |

---

## Important Interview Clarification

Linked List insertion and deletion are not always O(1).

They are O(1) only when:

```txt
the node/reference is already given
```

They become O(n) when:

```txt
we need to search for the position first
```

Example:

```txt
Insert after a given node → O(1)
Insert after finding a value → O(n)
```

This is a common interview trap.

---

## Space Complexity Thinking

Most basic linked list operations use only a few pointers:

```txt
current
previous
next
slow
fast
dummy
```

So space is usually:

```txt
O(1)
```

But if we use:

```txt
HashSet
HashMap
Recursion
Extra array/list
```

then space may become:

```txt
O(n)
```

---

## Edge Cases Affecting Complexity

Always test these cases:

```txt
empty list
single node list
two node list
target at head
target at tail
target not present
cycle present
cycle absent
```

These may not change Big-O complexity, but they affect correctness.

---

## Complexity Mistakes Beginners Make

| Mistake | Correct Thinking |
|---|---|
| Linked list access is O(1) | Access is O(n) |
| Insert/delete is always O(1) | Only O(1) if node is already available |
| Tail insertion is always O(1) | Only if tail pointer exists |
| Recursive reverse is O(1) space | Recursive call stack takes O(n) |
| Extra HashSet does not count | HashSet uses O(n) space |
| One loop always means easy | Pointer logic still matters |

---

## Complexity Decision Guide

Ask this before solving:

```txt
Do I visit every node?
→ O(n)

Do I only change head?
→ O(1)

Do I search first and then insert/delete?
→ O(n)

Do I already have the node?
→ O(1) for link change

Do I use HashMap/HashSet?
→ O(n) space

Do I use recursion?
→ O(n) stack space
```

---

## Day 1 Complexity Revision

```txt
Access by index → O(n)
Search → O(n)
Traversal → O(n)
Find length → O(n)
Insert at head → O(1)
Delete head → O(1)
Insert/delete after known node → O(1)
Insert/delete after search → O(n)
Iterative reverse → O(n), O(1)
Recursive reverse → O(n), O(n)
```

---

## Final Checklist

| Skill | Status |
|---|---|
| Understand access complexity | ✅ |
| Understand search complexity | ✅ |
| Understand traversal complexity | ✅ |
| Understand insertion complexity | ✅ |
| Understand deletion complexity | ✅ |
| Understand tail pointer impact | ✅ |
| Understand O(1) vs O(n) trap | ✅ |
| Understand space complexity | ✅ |
| Understand edge cases | ✅ |
