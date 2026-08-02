# Day 6 Practice: Two Pointers Gap Pattern

This practice file is for Pattern 04 of Linked List.

The goal is to become comfortable with maintaining a fixed gap between two pointers.

Focus on:

```txt
moving fast pointer first
keeping slow at head initially
maintaining fixed gap
finding nth node from end
removing nth node from end
using dummy node for deletion
handling off-by-one errors
```

---

## Practice Method

For every problem, write:

```txt
What is n or k?
How many steps should fast move first?
Should dummy node be used?
Where should slow stop?
When does the loop stop?
What should be returned?
Time complexity:
Space complexity:
```

---

## Practice 1: Find 2nd Node From End

Given:

```txt
head → 10 → 20 → 30 → 40 → 50 → null
n = 2
```

Answer:

```txt
40
```

Reason:

```txt
From the end:
1st = 50
2nd = 40
```

Gap setup:

```txt
Move fast 2 steps ahead.
Then move fast and slow together.
```

---

## Practice 2: Dry Run Find 2nd From End

Input:

```txt
10 → 20 → 30 → 40 → 50 → null
n = 2
```

After moving fast 2 steps:

```txt
slow = 10
fast = 30
```

Move together:

| Step | slow | fast |
|---:|---:|---:|
| 1 | 20 | 40 |
| 2 | 30 | 50 |
| 3 | 40 | null |

Answer:

```txt
40
```

---

## Practice 3: Find 1st Node From End

Given:

```txt
head → 5 → 10 → 15 → null
n = 1
```

Answer:

```txt
15
```

Reason:

```txt
1st node from end is the last node.
```

---

## Practice 4: Find 3rd Node From End

Given:

```txt
head → 5 → 10 → 15 → null
n = 3
```

Answer:

```txt
5
```

Reason:

```txt
3rd node from end is the head.
```

---

## Practice 5: Invalid N Greater Than Length

Given:

```txt
head → 5 → 10 → 15 → null
n = 4
```

Answer:

```txt
null
```

Reason:

```txt
The list has only 3 nodes.
4th node from end does not exist.
```

---

## Practice 6: Empty List

Given:

```txt
head → null
n = 1
```

Answer:

```txt
null
```

Reason:

```txt
There is no node in the list.
```

---

## Practice 7: Find Kth From End

Given:

```txt
head → 1 → 2 → 3 → 4 → 5 → 6 → null
k = 4
```

Answer:

```txt
3
```

Reason:

```txt
From end:
1st = 6
2nd = 5
3rd = 4
4th = 3
```

---

## Practice 8: Remove 2nd Node From End

Given:

```txt
head → 10 → 20 → 30 → 40 → 50 → null
n = 2
```

Remove:

```txt
40
```

Output:

```txt
head → 10 → 20 → 30 → 50 → null
```

Use:

```txt
dummy
fast
slow
```

---

## Practice 9: Dry Run Remove 2nd From End

Input:

```txt
dummy → 10 → 20 → 30 → 40 → 50 → null
n = 2
```

Move fast `n + 1 = 3` steps:

| Step | fast |
|---:|---|
| 1 | 10 |
| 2 | 20 |
| 3 | 30 |

Now:

```txt
slow = dummy
fast = 30
```

Move together:

| Step | slow | fast |
|---:|---|---|
| 1 | 10 | 40 |
| 2 | 20 | 50 |
| 3 | 30 | null |

Now:

```txt
slow = 30
slow.next = 40
```

Delete:

```java
slow.next = slow.next.next;
```

Output:

```txt
10 → 20 → 30 → 50 → null
```

---

## Practice 10: Remove Head From End

Given:

```txt
head → 10 → 20 → 30 → null
n = 3
```

Remove:

```txt
10
```

Output:

```txt
head → 20 → 30 → null
```

Why dummy is needed:

```txt
The node to remove is head.
```

With dummy:

```txt
dummy → 10 → 20 → 30 → null
```

After deletion:

```txt
dummy → 20 → 30 → null
```

Return:

```java
dummy.next
```

---

## Practice 11: Remove Last Node

Given:

```txt
head → 10 → 20 → 30 → null
n = 1
```

Remove:

```txt
30
```

Output:

```txt
head → 10 → 20 → null
```

Reason:

```txt
1st node from end is the last node.
```

---

## Practice 12: Remove Only Node

Given:

```txt
head → 10 → null
n = 1
```

Output:

```txt
null
```

With dummy:

```txt
dummy → 10 → null
```

Delete:

```java
dummy.next = dummy.next.next;
```

Now:

```txt
dummy → null
```

Return:

```txt
dummy.next
```

---

## Practice 13: Find Previous of 2nd Node From End

Given:

```txt
head → 10 → 20 → 30 → 40 → 50 → null
n = 2
```

Nth node from end:

```txt
40
```

Previous node:

```txt
30
```

Answer:

```txt
30
```

Use:

```txt
dummy + n + 1 gap
```

---

## Practice 14: Move Pointer K Steps

Given:

```txt
node → 10 → 20 → 30 → 40 → null
k = 2
```

After moving 2 steps:

```txt
30
```

Dry run:

| Step | current |
|---:|---|
| start | 10 |
| 1 | 20 |
| 2 | 30 |

---

## Practice 15: Check At Least K Nodes

Given:

```txt
head → 1 → 2 → 3 → null
k = 3
```

Answer:

```txt
true
```

Given:

```txt
head → 1 → 2 → 3 → null
k = 4
```

Answer:

```txt
false
```

---

## Practice 16: Align Two Lists by Length Gap

Given:

```txt
List A:
1 → 2 → 3 → 4 → 5 → null

List B:
9 → 8 → 4 → 5 → null
```

Lengths:

```txt
Length A = 5
Length B = 4
Gap = 1
```

Move longer list pointer:

```txt
pointerA moves from 1 to 2
```

Now both remaining lengths are equal.

---

## Practice 17: Identify Pattern Signal

Problem:

```txt
Given the head of a linked list, return the kth node from the end.
```

Answer:

```txt
Pattern: Two Pointers Gap
Reason: It asks for a node from the end.
```

---

## Practice 18: Identify Pattern Signal

Problem:

```txt
Given the head of a linked list, find the middle node.
```

Answer:

```txt
Pattern: Fast and Slow Pointers
Reason: It asks for middle, not fixed gap.
```

This is not the gap pattern.

---

## Practice 19: Identify Pattern Signal

Problem:

```txt
Given head, remove the nth node from the end.
```

Answer:

```txt
Pattern: Two Pointers Gap + Dummy Node
Reason: Need nth from end and deletion may affect head.
```

---

## Practice 20: Fill the Blank — Find Nth From End

Complete:

```java
ListNode fast = head;
ListNode slow = head;

for (int i = 0; i < n; i++) {
    fast = _____;
}

while (fast != null) {
    fast = fast.next;
    slow = _____;
}
```

Answer:

```java
ListNode fast = head;
ListNode slow = head;

for (int i = 0; i < n; i++) {
    fast = fast.next;
}

while (fast != null) {
    fast = fast.next;
    slow = slow.next;
}
```

---

## Practice 21: Fill the Blank — Remove Nth From End

Complete:

```java
ListNode dummy = new ListNode(0);
dummy.next = head;

ListNode fast = dummy;
ListNode slow = dummy;

for (int i = 0; i <= n; i++) {
    fast = fast.next;
}

while (fast != null) {
    fast = fast.next;
    slow = slow.next;
}

slow.next = _____;

return _____;
```

Answer:

```java
slow.next = slow.next.next;

return dummy.next;
```

---

## Practice 22: Why Move Fast First?

Question:

```txt
Why do we move fast first in the gap pattern?
```

Answer:

```txt
To create a fixed distance between fast and slow.

After the gap is created, both pointers move together while maintaining that distance.
```

---

## Practice 23: Why Use Dummy for Deletion?

Question:

```txt
Why do we use dummy while removing nth node from end?
```

Answer:

```txt
Because the node to delete may be the head.

Dummy gives us a stable previous node before head.
```

---

## Practice 24: Why Move Fast n + 1 Steps for Deletion?

Question:

```txt
Why do we move fast n + 1 steps from dummy?
```

Answer:

```txt
Because slow must stop before the node to delete.

Deleting requires:
slow.next = slow.next.next
```

---

## Practice 25: Identify the Bug

Wrong code:

```java
ListNode fast = head;
ListNode slow = head;

while (fast != null) {
    fast = fast.next;
    slow = slow.next;
}
```

Question:

```txt
What is wrong for finding nth node from end?
```

Answer:

```txt
No gap was created first.

Both pointers start together, so slow will become null when fast becomes null.
```

Correct idea:

```txt
Move fast n steps first.
```

---

## Practice 26: Identify the Bug

Wrong code:

```java
for (int i = 0; i < n; i++) {
    fast = fast.next;
}
```

Question:

```txt
What can go wrong?
```

Answer:

```txt
If n is greater than the list length, fast may become null and fast.next can cause NullPointerException later.
```

Correct:

```java
for (int i = 0; i < n; i++) {
    if (fast == null) {
        return null;
    }

    fast = fast.next;
}
```

---

## Practice 27: Identify the Bug

Wrong code:

```java
slow.next = slow.next.next;
return head;
```

Question:

```txt
Why can this be wrong while removing nth node from end?
```

Answer:

```txt
If the removed node is head, returning old head is wrong.

Use dummy and return dummy.next.
```

---

## Practice 28: Gap vs Fast-Slow MCQ

### Q1. Which pattern finds nth node from end?

```txt
A. Traversal only
B. Two Pointers Gap
C. Binary Search
D. Prefix Sum
```

Answer:

```txt
B. Two Pointers Gap
```

---

### Q2. In gap pattern, what happens first?

```txt
A. Move slow first
B. Move fast fixed steps ahead
C. Reverse the list
D. Sort the list
```

Answer:

```txt
B. Move fast fixed steps ahead
```

---

### Q3. Why dummy is used in remove nth from end?

```txt
A. To sort the list
B. To handle head deletion
C. To count duplicate values
D. To create a cycle
```

Answer:

```txt
B. To handle head deletion
```

---

### Q4. What is the time complexity of finding nth from end?

```txt
A. O(1)
B. O(log n)
C. O(n)
D. O(n²)
```

Answer:

```txt
C. O(n)
```

---

### Q5. What is the space complexity of gap pointer pattern?

```txt
A. O(1)
B. O(n)
C. O(log n)
D. O(n²)
```

Answer:

```txt
A. O(1)
```

---

## Practice 29: Complexity Check

Fill the table:

| Operation | Time | Space |
|---|---:|---:|
| Find nth from end | O(n) | O(1) |
| Find kth from end | O(n) | O(1) |
| Remove nth from end | O(n) | O(1) |
| Delete kth from end | O(n) | O(1) |
| Move pointer k steps | O(k) | O(1) |
| Check at least k nodes | O(k) | O(1) |
| Align two lists by gap | O(n + m) | O(1) |

---

## Practice 30: Mini Coding Problem Set

Try writing code for these without looking at templates.

```txt
1. Move a pointer k steps
2. Check if a linked list has at least k nodes
3. Find nth node from end
4. Find kth node from end
5. Find value of nth node from end
6. Remove nth node from end
7. Delete kth node from end
8. Find previous of nth node from end
9. Move longer list pointer by length gap
10. Align two list pointers by length difference
```

---

## Practice 31: Edge Case Checklist

Test gap pointer solutions on:

```txt
head = null
head = 10 → null
n = 1
n = length
n > length
n = 0
remove head
remove tail
remove middle node
two-node list
odd length list
even length list
```

---

## Practice 32: Off-by-One Checklist

Before submitting, check:

```txt
For finding nth from end:
Did fast move exactly n steps?

For deleting nth from end:
Did fast move n + 1 steps from dummy?

Did slow stop at the answer node or before the node to delete?

Did I return slow for finding?
Did I return dummy.next for deletion?
```

---

## Practice 33: Dry Run Table Template

Use this table for any gap problem.

```txt
Linked list:
n or k:
Initial slow:
Initial fast:
Fast movement count:
Gap created:
Loop stop condition:
Final slow:
Answer:
```

Example:

```txt
Linked list: 10 → 20 → 30 → 40 → 50 → null
n = 2
Initial slow: 10
Initial fast: 10
Fast movement count: 2
Gap created: fast at 30, slow at 10
Loop stop condition: fast == null
Final slow: 40
Answer: 40
```

---

## Common Mistakes to Avoid

| Mistake | Correct Thinking |
|---|---|
| Not creating gap first | Move fast first |
| Moving fast two steps | That is fast-slow, not gap |
| Not checking invalid n | Handle n <= 0 and n > length |
| Removing without dummy | Head deletion may fail |
| Slow stops at wrong node | Check if you need node or previous node |
| Returning old head after deletion | Return dummy.next |
| Forgetting null checks | Avoid NullPointerException |

---

## Day 6 Final Revision

```txt
Two Pointers Gap Pattern:

fast moves first
slow waits
gap is created
then both move together

Find nth from end:
fast moves n steps
slow becomes answer

Remove nth from end:
dummy is used
fast moves n + 1 steps from dummy
slow becomes previous of target
delete slow.next
return dummy.next
```

---

## Day 6 Completion Checklist

| Task | Status |
|---|---|
| Understand fixed gap idea | ✅ |
| Move fast pointer first | ✅ |
| Find nth node from end | ✅ |
| Find kth node from end | ✅ |
| Remove nth node from end | ✅ |
| Delete kth node from end | ✅ |
| Use dummy for deletion | ✅ |
| Handle head removal | ✅ |
| Handle invalid n | ✅ |
| Understand gap vs fast-slow | ✅ |
| Avoid off-by-one errors | ✅ |
| Understand time complexity | ✅ |
| Understand space complexity | ✅ |
