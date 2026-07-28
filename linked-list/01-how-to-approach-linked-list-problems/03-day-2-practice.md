# Day 2 Practice: How to Approach Linked List Problems

This practice file is designed to train your thinking before writing code.

The goal is not to solve all linked list patterns today.

The goal is to learn how to identify:

```txt
problem signal
possible pattern
required pointers
head change possibility
edge cases
return type
```

---

## Practice Method

For every problem statement, fill this:

```txt
Problem signal:
Can head change?
Pointers needed:
Likely pattern:
Return type:
Edge cases:
```

This is how you build linked list problem-solving skill.

---

## Practice 1: Find Length

Problem:

```txt
Given the head of a linked list, return the number of nodes.
```

Fill:

```txt
Problem signal:
Can head change?
Pointers needed:
Likely pattern:
Return type:
Edge cases:
```

Answer:

```txt
Problem signal: count nodes
Can head change? No
Pointers needed: current, length
Likely pattern: Traversal
Return type: int
Edge cases: empty list, single node
```

---

## Practice 2: Search Target

Problem:

```txt
Given the head of a linked list and an integer target, return true if target exists.
```

Answer:

```txt
Problem signal: search value
Can head change? No
Pointers needed: current
Likely pattern: Traversal / Search
Return type: boolean
Edge cases: empty list, target at head, target at tail, target not present
```

---

## Practice 3: Delete a Value

Problem:

```txt
Given the head of a linked list and a value target, delete all nodes with that value.
```

Answer:

```txt
Problem signal: delete nodes by value
Can head change? Yes
Pointers needed: dummy, current
Likely pattern: Dummy Node + Pointer Rewiring
Return type: ListNode
Edge cases: empty list, target at head, all nodes are target, target not present
```

---

## Practice 4: Reverse a List

Problem:

```txt
Given the head of a linked list, reverse the linked list and return the new head.
```

Answer:

```txt
Problem signal: reverse links
Can head change? Yes
Pointers needed: previous, current, nextNode
Likely pattern: Linked List Reversal
Return type: ListNode
Edge cases: empty list, single node, two nodes
```

---

## Practice 5: Find Middle

Problem:

```txt
Given the head of a linked list, return the middle node.
```

Answer:

```txt
Problem signal: middle node
Can head change? No
Pointers needed: slow, fast
Likely pattern: Fast and Slow Pointers
Return type: ListNode
Edge cases: empty list, single node, even length, odd length
```

---

## Practice 6: Detect Cycle

Problem:

```txt
Given the head of a linked list, return true if the linked list has a cycle.
```

Answer:

```txt
Problem signal: cycle
Can head change? No
Pointers needed: slow, fast
Likely pattern: Cycle Detection / Floyd’s Algorithm
Return type: boolean
Edge cases: empty list, single node, cycle exists, no cycle
```

---

## Practice 7: Remove Nth Node From End

Problem:

```txt
Given the head of a linked list, remove the nth node from the end.
```

Answer:

```txt
Problem signal: nth from end, remove node
Can head change? Yes
Pointers needed: dummy, fast, slow
Likely pattern: Two Pointers Gap + Dummy Node
Return type: ListNode
Edge cases: remove head, remove tail, n equals length, single node
```

---

## Practice 8: Merge Two Sorted Lists

Problem:

```txt
Given two sorted linked lists, merge them into one sorted linked list.
```

Answer:

```txt
Problem signal: two sorted lists, merge
Can head change? New head created
Pointers needed: dummy, tail, list1, list2
Likely pattern: Merge Pattern
Return type: ListNode
Edge cases: one list empty, both empty, duplicate values
```

---

## Practice 9: Check Palindrome

Problem:

```txt
Given the head of a linked list, return true if it is a palindrome.
```

Answer:

```txt
Problem signal: palindrome
Can head change? Usually no final change, but second half may be reversed temporarily
Pointers needed: slow, fast, previous, current
Likely pattern: Fast-Slow + Reversal + Compare
Return type: boolean
Edge cases: empty list, single node, even length, odd length
```

---

## Practice 10: Intersection of Two Lists

Problem:

```txt
Given the heads of two linked lists, find the node where they intersect.
```

Answer:

```txt
Problem signal: two lists, intersection
Can head change? No
Pointers needed: pointerA, pointerB
Likely pattern: Intersection / Pointer Switching
Return type: ListNode
Edge cases: no intersection, intersection at head, different lengths
```

---

## Practice 11: Identify Pointer Setup

Choose the best pointer setup.

### Q1. Reverse linked list

Options:

```txt
A. slow and fast
B. previous, current, nextNode
C. dummy and tail
D. left and right indexes
```

Answer:

```txt
B. previous, current, nextNode
```

---

### Q2. Find middle node

Options:

```txt
A. slow and fast
B. dummy and tail
C. previous and nextNode only
D. HashMap only
```

Answer:

```txt
A. slow and fast
```

---

### Q3. Remove head safely

Options:

```txt
A. dummy node
B. binary search
C. prefix sum
D. sorting
```

Answer:

```txt
A. dummy node
```

---

### Q4. Merge two sorted linked lists

Options:

```txt
A. dummy and tail
B. slow and fast
C. previous and current only
D. stack
```

Answer:

```txt
A. dummy and tail
```

---

## Practice 12: Can Head Change?

Mark Yes or No.

| Problem | Can Head Change? | Reason |
|---|---|---|
| Find length | No | Only counting |
| Search value | No | Only checking |
| Delete first node | Yes | Head moves to next |
| Reverse list | Yes | Last node becomes new head |
| Merge two lists | Yes | New result head |
| Detect cycle | No | Only checking |
| Remove nth from end | Yes | If nth node from end is head |

---

## Practice 13: Choose the Pattern

| Problem Statement | Pattern |
|---|---|
| Return number of nodes | Traversal |
| Return middle node | Fast and Slow Pointers |
| Detect loop | Cycle Detection |
| Remove nth node from end | Two Pointers Gap + Dummy Node |
| Reverse full list | Linked List Reversal |
| Merge two sorted lists | Merge Pattern |
| Delete all target nodes | Dummy Node + Pointer Rewiring |
| Add two numbers represented by lists | Carry Pattern |

---

## Practice 14: Edge Case Checklist

For each future linked list solution, test:

```txt
head = null
head = 10 → null
head = 10 → 20 → null
target at head
target at tail
target not present
even length list
odd length list
```

Why?

```txt
Most linked list bugs happen at boundaries.
```

---

## Practice 15: Dry Run Pointer Movement

Linked list:

```txt
head → 10 → 20 → 30 → null
```

Initial:

```txt
previous = null
current = 10
```

Move one step:

```java
previous = current;
current = current.next;
```

Fill:

```txt
previous =
current =
```

Answer:

```txt
previous = 10
current = 20
```

Move again:

Answer:

```txt
previous = 20
current = 30
```

Move again:

Answer:

```txt
previous = 30
current = null
```

---

## Practice 16: Safe Rewiring Question

Before changing:

```java
current.next = previous;
```

what should you store?

Answer:

```txt
current.next should be stored in nextNode before changing the link.
```

Correct:

```java
ListNode nextNode = current.next;
current.next = previous;
```

---

## Practice 17: Dummy Node Question

Why do we use dummy node?

Answer:

```txt
Dummy node helps when the head may change.

It makes deletion, merge, and new list construction easier.
```

Return value when dummy is used:

```java
return dummy.next;
```

---

## Practice 18: Fast-Slow Safety Check

Why do we write:

```java
while (fast != null && fast.next != null)
```

Answer:

```txt
Because fast moves two steps.

We must make sure fast and fast.next are not null before accessing fast.next.next.
```

---

## Practice 19: Mini Approach Worksheet

Problem:

```txt
Given head, remove all duplicate values from a sorted linked list.
```

Fill:

```txt
Problem signal:
Can head change?
Pointers needed:
Likely pattern:
Return type:
Edge cases:
```

Suggested answer:

```txt
Problem signal: sorted list, duplicates, remove nodes
Can head change? Usually no for simple duplicate removal, but can depend on version
Pointers needed: current
Likely pattern: Traversal + Pointer Rewiring
Return type: ListNode
Edge cases: empty list, single node, all duplicates, no duplicates
```

---

## Practice 20: Mini Approach Worksheet

Problem:

```txt
Given head, reorder the list as L0 → Ln → L1 → Ln-1 ...
```

Fill:

```txt
Problem signal:
Can head change?
Pointers needed:
Likely pattern:
Return type:
Edge cases:
```

Suggested answer:

```txt
Problem signal: reorder first and last nodes
Can head change? Usually head remains same
Pointers needed: slow, fast, previous, current, first, second
Likely pattern: List Weaving and Reordering
Return type: ListNode or void depending on problem
Edge cases: empty list, single node, two nodes, odd/even length
```

---

## Day 2 Final Revision

```txt
Read problem carefully
Find signal words
Check if head can change
Choose pointer setup
Draw the list
Dry run before code
Use dummy for head edge cases
Use slow-fast for middle/cycle
Use gap pointers for nth from end
Use prev-current-next for reversal
Return the correct head
```

---

## Day 2 Completion Checklist

| Task | Status |
|---|---|
| Identify problem signal | ✅ |
| Decide if head can change | ✅ |
| Choose pointer setup | ✅ |
| Identify likely pattern | ✅ |
| Understand dummy node use | ✅ |
| Understand slow-fast use | ✅ |
| Understand gap pointer use | ✅ |
| Understand safe rewiring | ✅ |
| Practice edge cases | ✅ |
| Build approach before code | ✅ |
