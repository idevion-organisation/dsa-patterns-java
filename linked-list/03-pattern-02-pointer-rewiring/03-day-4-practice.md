# Day 4 Practice: Pointer Rewiring, Insertion, Deletion and Swapping

This practice file is for Pattern 02 of Linked List.

The goal is to build confidence in changing links safely.

Focus on:

```txt
insertion
deletion
skipping nodes
swapping nodes
head changes
safe next pointer handling
```

Do not memorize code.

Dry run every pointer change.

---

## Practice Method

For every problem, write:

```txt
Can head change?
Which node is current?
Which node is previous?
Which link will change?
Do I need to save nextNode?
What should be returned?
Time complexity:
Space complexity:
```

---

## Practice 1: Insert at Head

Given:

```txt
head → 10 → 20 → 30 → null
value = 5
```

After insertion:

```txt
head → 5 → 10 → 20 → 30 → null
```

Pointer steps:

```txt
newNode.next = head
head = newNode
```

Complexity:

```txt
Time Complexity: O(1)
Space Complexity: O(1)
```

---

## Practice 2: Insert at Head in Empty List

Given:

```txt
head → null
value = 10
```

After insertion:

```txt
head → 10 → null
```

Reason:

```txt
newNode.next points to null
head becomes newNode
```

---

## Practice 3: Insert at Tail

Given:

```txt
head → 10 → 20 → 30 → null
value = 40
```

After insertion:

```txt
head → 10 → 20 → 30 → 40 → null
```

Which node should current stop at?

```txt
30
```

Why?

```txt
30 is the last node because 30.next is null.
```

---

## Practice 4: Insert at Tail in Empty List

Given:

```txt
head → null
value = 100
```

After insertion:

```txt
head → 100 → null
```

Return:

```txt
newNode
```

---

## Practice 5: Insert After Value

Given:

```txt
head → 10 → 20 → 30 → null
target = 20
value = 25
```

After insertion:

```txt
head → 10 → 20 → 25 → 30 → null
```

Correct order:

```java
newNode.next = current.next;
current.next = newNode;
```

Why this order?

```txt
Because newNode must first connect to the remaining list.
```

---

## Practice 6: Insert After Value Not Found

Given:

```txt
head → 10 → 20 → 30 → null
target = 50
value = 60
```

Answer:

```txt
List remains unchanged.
```

Result:

```txt
head → 10 → 20 → 30 → null
```

---

## Practice 7: Delete Head

Given:

```txt
head → 10 → 20 → 30 → null
```

After deletion:

```txt
head → 20 → 30 → null
```

Pointer step:

```java
head = head.next;
```

Return:

```txt
head
```

Complexity:

```txt
O(1)
```

---

## Practice 8: Delete Head From Single Node List

Given:

```txt
head → 10 → null
```

After deletion:

```txt
head → null
```

Return:

```txt
null
```

---

## Practice 9: Delete Tail

Given:

```txt
head → 10 → 20 → 30 → null
```

After deletion:

```txt
head → 10 → 20 → null
```

Which node should current stop at?

```txt
20
```

Why?

```txt
20 is the second last node.
```

Pointer step:

```java
current.next = null;
```

---

## Practice 10: Delete Tail From Single Node List

Given:

```txt
head → 10 → null
```

After deleting tail:

```txt
head → null
```

Reason:

```txt
The only node is both head and tail.
```

---

## Practice 11: Delete First Value

Given:

```txt
head → 10 → 20 → 30 → 20 → null
target = 20
```

After deletion:

```txt
head → 10 → 30 → 20 → null
```

Pointer state when target is found:

```txt
previous = 10
current = 20
```

Rewiring:

```java
previous.next = current.next;
```

Meaning:

```txt
10.next = 30
```

---

## Practice 12: Delete First Value at Head

Given:

```txt
head → 10 → 20 → 30 → null
target = 10
```

After deletion:

```txt
head → 20 → 30 → null
```

Return:

```txt
head.next
```

Why?

```txt
Target node is the head, so head changes.
```

---

## Practice 13: Delete Value Not Present

Given:

```txt
head → 10 → 20 → 30 → null
target = 50
```

After deletion:

```txt
head → 10 → 20 → 30 → null
```

Reason:

```txt
Target was not found.
```

---

## Practice 14: Delete All Values

Given:

```txt
head → 20 → 20 → 10 → 20 → 30 → null
target = 20
```

After deletion:

```txt
head → 10 → 30 → null
```

Important:

```txt
Multiple head nodes can also be deleted.
```

Correct first step:

```java
while (head != null && head.val == target) {
    head = head.next;
}
```

---

## Practice 15: Delete All Values With Consecutive Targets

Given:

```txt
head → 10 → 20 → 20 → 20 → 30 → null
target = 20
```

After deletion:

```txt
head → 10 → 30 → null
```

Why should we not move current after deletion?

```txt
Because current.next may again be a target.
```

Correct logic:

```java
if (current.next.val == target) {
    current.next = current.next.next;
} else {
    current = current.next;
}
```

---

## Practice 16: Insert at Position

Given:

```txt
head → 10 → 20 → 30 → null
position = 1
value = 15
```

After insertion:

```txt
head → 10 → 15 → 20 → 30 → null
```

Stop current at:

```txt
position - 1 = 0
```

So current should be:

```txt
10
```

---

## Practice 17: Insert at Position 0

Given:

```txt
head → 10 → 20 → null
position = 0
value = 5
```

After insertion:

```txt
head → 5 → 10 → 20 → null
```

Return:

```txt
newNode
```

---

## Practice 18: Delete at Position

Given:

```txt
head → 10 → 20 → 30 → 40 → null
position = 2
```

After deletion:

```txt
head → 10 → 20 → 40 → null
```

Stop current at:

```txt
position - 1 = 1
```

So current should be:

```txt
20
```

Rewiring:

```java
current.next = current.next.next;
```

---

## Practice 19: Delete at Position 0

Given:

```txt
head → 10 → 20 → 30 → null
position = 0
```

After deletion:

```txt
head → 20 → 30 → null
```

Return:

```txt
head.next
```

---

## Practice 20: Swap First Two Nodes

Given:

```txt
head → 10 → 20 → 30 → null
```

After swap:

```txt
head → 20 → 10 → 30 → null
```

Pointers:

```txt
first = 10
second = 20
third = 30
```

Rewiring:

```java
second.next = first;
first.next = third;
```

Return:

```txt
second
```

---

## Practice 21: Swap First Two Nodes in Single Node List

Given:

```txt
head → 10 → null
```

After swap:

```txt
head → 10 → null
```

Reason:

```txt
There are not enough nodes to swap.
```

---

## Practice 22: Swap Nodes or Values?

Question:

```txt
If we only swap val fields of two nodes, is it pointer rewiring?
```

Answer:

```txt
No.
```

Reason:

```txt
Pointer rewiring means changing next references, not just values.
```

---

## Practice 23: Identify the Bug

Wrong code:

```java
current.next = newNode;
newNode.next = current.next;
```

Question:

```txt
What is wrong?
```

Answer:

```txt
The original next node may be lost.

Also, newNode.next may point incorrectly.
```

Correct code:

```java
newNode.next = current.next;
current.next = newNode;
```

---

## Practice 24: Identify the Bug

Wrong code:

```java
while (current.next != null) {
    if (current.next.val == target) {
        current.next = current.next.next;
    }

    current = current.next;
}
```

Problem:

```txt
It always moves current even after deletion.
```

Why is this bad?

```txt
It can skip consecutive target nodes.
```

Correct:

```java
while (current != null && current.next != null) {
    if (current.next.val == target) {
        current.next = current.next.next;
    } else {
        current = current.next;
    }
}
```

---

## Practice 25: Fill the Blank — Insert After Current

Complete the code:

```java
ListNode newNode = new ListNode(value);

newNode.next = _____;
current.next = _____;
```

Answer:

```java
ListNode newNode = new ListNode(value);

newNode.next = current.next;
current.next = newNode;
```

---

## Practice 26: Fill the Blank — Delete Current

Given:

```txt
previous → current → nextNode
```

Complete:

```java
previous.next = _____;
```

Answer:

```java
previous.next = current.next;
```

---

## Practice 27: Fill the Blank — Delete Next Node

Given:

```txt
current → nodeToDelete → nextNode
```

Complete:

```java
current.next = _____;
```

Answer:

```java
current.next = current.next.next;
```

---

## Practice 28: Remove Duplicates From Sorted List

Given:

```txt
head → 1 → 1 → 2 → 3 → 3 → null
```

After removing duplicates:

```txt
head → 1 → 2 → 3 → null
```

Reason:

```txt
Duplicates are adjacent because the list is sorted.
```

Pointer rule:

```java
if (current.val == current.next.val) {
    current.next = current.next.next;
} else {
    current = current.next;
}
```

---

## Practice 29: Skip Alternate Nodes

Given:

```txt
head → 1 → 2 → 3 → 4 → 5 → null
```

After skipping alternate nodes:

```txt
head → 1 → 3 → 5 → null
```

Pointer rule:

```java
current.next = current.next.next;
current = current.next;
```

---

## Practice 30: Complexity Check

Fill the table:

| Operation | Time | Space |
|---|---:|---:|
| Insert at head | O(1) | O(1) |
| Delete head | O(1) | O(1) |
| Insert at tail | O(n) | O(1) |
| Delete tail | O(n) | O(1) |
| Insert after value | O(n) | O(1) |
| Delete first value | O(n) | O(1) |
| Delete all values | O(n) | O(1) |
| Insert at position | O(n) | O(1) |
| Delete at position | O(n) | O(1) |
| Swap first two nodes | O(1) | O(1) |

---

## Practice 31: MCQ Check

### Q1. What does pointer rewiring mean?

```txt
A. Sorting values
B. Changing next references
C. Using binary search
D. Creating arrays
```

Answer:

```txt
B. Changing next references
```

---

### Q2. Which pointer is needed to delete current node?

```txt
A. previous
B. index only
C. pivot
D. random
```

Answer:

```txt
A. previous
```

---

### Q3. What should be done before changing `current.next` in risky cases?

```txt
A. Delete head always
B. Save next node if needed
C. Sort the list
D. Use array indexing
```

Answer:

```txt
B. Save next node if needed
```

---

### Q4. What is the time complexity of insert at head?

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

### Q5. What should we return after swapping first two nodes?

```txt
A. first
B. second
C. third
D. null always
```

Answer:

```txt
B. second
```

---

## Practice 32: Mini Coding Problem Set

Try writing code for these without looking at templates.

```txt
1. Insert at head
2. Insert at tail
3. Insert after target value
4. Insert at position
5. Delete head
6. Delete tail
7. Delete first target value
8. Delete all target values
9. Delete at position
10. Remove duplicates from sorted list
11. Skip alternate nodes
12. Swap first two nodes
```

---

## Practice 33: Edge Case Checklist

Test every pointer rewiring solution on:

```txt
head = null
head = 10 → null
head = 10 → 20 → null
target at head
target at tail
target in middle
target not present
all nodes are target
consecutive target nodes
invalid position
position = 0
```

---

## Practice 34: Rewiring Safety Checklist

Before submitting, check:

```txt
Did I handle head == null?
Did I handle head change?
Did I return the correct head?
Did I save nextNode if required?
Did I connect newNode before breaking old links?
Did I avoid moving current after deletion when needed?
Did I check current.next before using current.next.next?
Did I test single node list?
```

---

## Day 4 Final Revision

```txt
Pointer Rewiring = changing node links

Insert:
newNode.next = current.next
current.next = newNode

Delete:
previous.next = current.next

Delete next:
current.next = current.next.next

Swap:
second.next = first
first.next = third

Most important:
Never break links without knowing where the next node is.
```

---

## Day 4 Completion Checklist

| Task | Status |
|---|---|
| Understand pointer rewiring | ✅ |
| Insert at head | ✅ |
| Insert at tail | ✅ |
| Insert after value | ✅ |
| Insert at position | ✅ |
| Delete head | ✅ |
| Delete tail | ✅ |
| Delete first value | ✅ |
| Delete all values | ✅ |
| Delete at position | ✅ |
| Swap first two nodes | ✅ |
| Remove duplicates from sorted list | ✅ |
| Skip alternate nodes | ✅ |
| Understand head changes | ✅ |
| Avoid broken links | ✅ |
| Understand complexities | ✅ |
