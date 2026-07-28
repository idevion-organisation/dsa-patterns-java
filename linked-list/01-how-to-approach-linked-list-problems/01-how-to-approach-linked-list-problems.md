# How to Approach Linked List Problems

Linked List problems are not difficult because of syntax.

They become difficult because one wrong pointer move can break the whole list.

The main skill in linked list is not memorizing solutions.

The main skill is understanding:

```txt
where each pointer is
where each pointer should move
which link should be changed
whether head can change
whether null can appear
```

---

## Why Linked List Problems Feel Difficult

Many beginners struggle with linked list because:

```txt
there is no direct indexing
nodes are connected using references
head can change
links can break easily
null checks are important
dry run is visual, not index-based
```

In arrays, we think like this:

```txt
arr[i]
arr[i + 1]
arr[j]
```

In linked list, we think like this:

```txt
current
current.next
previous
nextNode
head
dummy
slow
fast
```

This is why linked list needs a different problem-solving approach.

---

## Core Rule

Before writing code, always draw the linked list.

Example:

```txt
head → 10 → 20 → 30 → 40 → null
```

Then mark pointers:

```txt
prev = null
current = 10
next = 20
```

If you cannot explain pointer movement on paper, writing code directly will usually cause mistakes.

---

## Linked List Problem-Solving Flow

Use this flow for almost every linked list problem:

```txt
1. Understand what the problem wants
2. Identify whether head can change
3. Decide which pointers are needed
4. Dry run with 3–4 nodes
5. Handle edge cases
6. Write code
7. Test empty, single-node, and multi-node cases
```

---

## Step 1: Understand the Problem

First ask:

```txt
Do I need to traverse?
Do I need to delete a node?
Do I need to insert a node?
Do I need to reverse links?
Do I need to find middle?
Do I need to detect a cycle?
Do I need to merge lists?
Do I need to return a modified head?
```

This helps you identify the correct pattern.

---

## Step 2: Check the Input Style

Most linked list problems give input like this:

```java
public ListNode solve(ListNode head) {

}
```

or:

```java
public ListNode solve(ListNode head1, ListNode head2) {

}
```

If the function returns `ListNode`, it usually means:

```txt
the list may be modified
head may change
new head should be returned
```

If the function returns `boolean`, `int`, or another value, it usually means:

```txt
the list may only need traversal or checking
```

---

## Step 3: Identify If Head Can Change

This is one of the most important questions.

Head can change when the problem asks to:

```txt
delete the first node
insert before the first node
reverse the list
remove elements
merge lists
sort lists
reorder lists
```

Example:

```txt
Original:
head → 10 → 20 → 30 → null

After reversing:
head → 30 → 20 → 10 → null
```

Here the head changes from `10` to `30`.

So the function must return the new head.

---

## Step 4: Choose the Right Pointers

Different linked list problems need different pointers.

| Pointer | Purpose |
|---|---|
| `current` | Traversal |
| `previous` | Tracks node before current |
| `nextNode` | Saves next node before changing links |
| `slow` | Moves one step |
| `fast` | Moves two steps |
| `dummy` | Handles head edge cases |
| `tail` | Builds a new list |
| `first` / `second` | Used when working with two halves or two lists |

---

## Basic Pointer Roles

### `current`

Used to visit nodes one by one.

```java
ListNode current = head;
```

### `previous`

Used when we need to delete or reverse links.

```java
ListNode previous = null;
```

### `nextNode`

Used when we are about to change `current.next`.

```java
ListNode nextNode = current.next;
```

### `dummy`

Used when head may change or edge cases are difficult.

```java
ListNode dummy = new ListNode(0);
dummy.next = head;
```

### `slow` and `fast`

Used for middle, cycle, and split problems.

```java
ListNode slow = head;
ListNode fast = head;
```

---

## Step 5: Dry Run Before Coding

For linked list, dry run is mandatory.

Do not dry run only values.

Dry run pointer positions.

Example:

```txt
head → 10 → 20 → 30 → null
```

Pointer dry run:

| Step | previous | current | nextNode |
|---:|---|---|---|
| Start | null | 10 | 20 |
| Move 1 | 10 | 20 | 30 |
| Move 2 | 20 | 30 | null |
| End | 30 | null | - |

This makes pointer movement clear.

---

## Step 6: Handle Edge Cases

Always test these cases:

```txt
head = null
head = single node
two nodes
target at head
target at tail
target not present
list length is even
list length is odd
```

Linked list problems often fail because of missing edge cases.

---

## Common Edge Cases

| Case | Why it matters |
|---|---|
| Empty list | `head == null` |
| Single node | `head.next == null` |
| Deleting head | Head changes |
| Deleting tail | Need previous node |
| Reversing list | Need to save next node |
| Finding middle | Even/odd length matters |
| Cycle detection | `fast` and `fast.next` must be checked |

---

## Step 7: Know the Major Linked List Pattern Families

This module will cover these pattern families:

```txt
Traversal, Search and Length
Pointer Rewiring
Dummy Node / Sentinel Node
Two Pointers Gap
Fast and Slow Pointers
Cycle Detection
Linked List Reversal
Advanced Reversal
Merge Pattern
Split and Merge Sort
Palindrome Checking
Intersection
Add Two Numbers / Carry
List Weaving and Reordering
Clone Random Pointer
```

Day 2 helps you understand how to approach all of them.

---

## Pattern Recognition Signals

| Problem Signal | Likely Pattern |
|---|---|
| Visit every node | Traversal |
| Find length/search value | Traversal |
| Delete/insert/swap nodes | Pointer Rewiring |
| Head deletion is possible | Dummy Node |
| Remove nth node from end | Two Pointers Gap |
| Find middle | Fast and Slow Pointers |
| Detect cycle | Cycle Detection |
| Reverse list | Linked List Reversal |
| Reverse between / k-group | Advanced Reversal |
| Merge sorted lists | Merge Pattern |
| Sort linked list | Split and Merge Sort |
| Check palindrome | Middle + Reverse + Compare |
| Find intersection | Pointer switching / length difference |
| Add numbers digit by digit | Carry Pattern |
| Reorder list | Split + Reverse + Merge |
| Random pointer copy | HashMap / Interleaving clone |

---

## How to Read a Linked List Problem

When reading the problem statement, underline these things mentally:

```txt
given head
return head
delete node
reverse
middle
cycle
merge
nth from end
sorted lists
two lists
random pointer
```

These words usually reveal the pattern.

---

## Example 1: Find Length

Problem:

```txt
Given the head of a linked list, return its length.
```

Signal:

```txt
visit every node
count nodes
```

Pattern:

```txt
Traversal
```

Pointers needed:

```txt
current
length
```

Return type:

```txt
int
```

---

## Example 2: Remove Nth Node From End

Problem:

```txt
Given the head of a linked list, remove the nth node from the end.
```

Signal:

```txt
nth from end
remove node
head may change
```

Pattern:

```txt
Two Pointers Gap + Dummy Node
```

Pointers needed:

```txt
dummy
slow
fast
```

Return type:

```txt
ListNode
```

---

## Example 3: Reverse Linked List

Problem:

```txt
Given the head of a linked list, reverse the list.
```

Signal:

```txt
reverse links
head will change
```

Pattern:

```txt
Linked List Reversal
```

Pointers needed:

```txt
previous
current
nextNode
```

Return type:

```txt
ListNode
```

---

## Example 4: Detect Cycle

Problem:

```txt
Given head, determine if the linked list has a cycle.
```

Signal:

```txt
cycle
loop
fast pointer may meet slow pointer
```

Pattern:

```txt
Cycle Detection / Floyd's Algorithm
```

Pointers needed:

```txt
slow
fast
```

Return type:

```txt
boolean
```

---

## Linked List Coding Mindset

Before coding, write this mentally:

```txt
What is the start?
What is the end condition?
Which pointer moves first?
Which pointer moves later?
Can head change?
Should I use dummy?
Do I need to save next?
What should I return?
```

---

## The Safe Rewiring Rule

Before changing any link:

```java
current.next = something;
```

ask:

```txt
Will I lose access to the rest of the list?
Should I store current.next first?
Can this create a cycle accidentally?
Can this skip a node accidentally?
```

For reversal, always save next first:

```java
ListNode nextNode = current.next;
current.next = previous;
previous = current;
current = nextNode;
```

---

## Why Dummy Node Helps

A dummy node is a fake node placed before the head.

```txt
dummy → head → 10 → 20 → 30 → null
```

It helps when the head might be deleted or changed.

Example:

```txt
remove all nodes with value 10
```

If the first node is also `10`, head changes.

Dummy node makes this easier:

```java
ListNode dummy = new ListNode(0);
dummy.next = head;
```

Return:

```java
return dummy.next;
```

---

## When to Use Dummy Node

Use dummy when:

```txt
head may be removed
new list is being built
merging lists
deleting nodes
handling many edge cases
```

Avoid dummy when:

```txt
you only need to traverse
you only need to count
you only need to search
```

---

## Why Fast and Slow Pointers Help

Fast and slow pointers help when one pointer needs to move faster than another.

Usually:

```txt
slow moves 1 step
fast moves 2 steps
```

Used for:

```txt
middle node
cycle detection
splitting list
palindrome linked list
```

---

## Why Two Pointers Gap Helps

Two pointers gap pattern is used when we need a fixed distance between two pointers.

Example:

```txt
remove nth node from end
```

Move `fast` ahead by `n` steps.

Then move both `fast` and `slow`.

When fast reaches the end, slow is near the target.

---

## Why Reversal Needs Three Pointers

To reverse links safely, we need:

```txt
previous
current
nextNode
```

Because once we change:

```java
current.next = previous;
```

we lose the original next connection unless we saved it.

That is why `nextNode` is important.

---

## Approach Template for Any Linked List Problem

Use this checklist:

```txt
1. Read the problem carefully
2. Identify return type
3. Check if head can change
4. Identify pattern signal
5. Choose pointers
6. Draw the list
7. Dry run with 3 nodes
8. Handle edge cases
9. Write code
10. Test manually
```

---

## Common Mistakes While Approaching

| Mistake | Correct Approach |
|---|---|
| Starting code immediately | Draw list first |
| Ignoring head changes | Ask if head can change |
| Not using dummy when needed | Use dummy for deletion/merge/head edge cases |
| Changing links without saving next | Store `nextNode` first |
| Checking only normal case | Test empty and single node |
| Confusing slow-fast and gap pointers | Identify exact signal |
| Returning wrong head | Return new head or `dummy.next` |

---

## Day 2 Learning Goal

After completing Day 2, you should be able to:

```txt
read a linked list problem
identify if head can change
choose the correct pointer setup
recognize common pattern signals
dry run pointer movement
avoid pointer-breaking mistakes
decide when dummy node is useful
understand how future linked list patterns connect
```

---

## Final Revision

```txt
Linked List approach = draw first, code later
Head can change = be careful with return
Deletion/merge = think dummy node
Middle/cycle = think slow-fast
Nth from end = think gap pointers
Reverse = think previous-current-next
Every pointer change must be dry run
```

---

## Day 2 Checklist

| Skill | Status |
|---|---|
| Understand linked list problem approach | ✅ |
| Identify head change cases | ✅ |
| Choose basic pointers | ✅ |
| Recognize pattern signals | ✅ |
| Understand dummy node purpose | ✅ |
| Understand slow-fast purpose | ✅ |
| Understand gap pointer purpose | ✅ |
| Understand safe rewiring rule | ✅ |
| Dry run pointer movement | ✅ |
