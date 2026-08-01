# Day 5 Practice: Dummy Node / Sentinel Node

This practice file is for Pattern 03 of Linked List.

The goal is to become comfortable with using a fake node before the head to simplify linked list modification.

Focus on:

```txt
dummy node creation
dummy.next connection
deleting current.next
building result using tail
returning dummy.next
handling head-changing cases
```

---

## Practice Method

For every problem, write:

```txt
Can head change?
Should dummy node be used?
Where should current start?
Are we deleting current or current.next?
Should current move after deletion?
What should be returned?
Time complexity:
Space complexity:
```

---

## Practice 1: Identify Dummy Node

Given:

```txt
head → 10 → 20 → 30 → null
```

After adding dummy:

```txt
dummy → 10 → 20 → 30 → null
```

Fill:

```txt
dummy.next =
real head =
return value =
```

Answer:

```txt
dummy.next = 10
real head = 10
return value = dummy.next
```

---

## Practice 2: Why Dummy Node?

Question:

```txt
Why do we use dummy node in linked list problems?
```

Answer:

```txt
Dummy node helps when head may change.

It gives a stable node before the head, so deleting or inserting near the beginning becomes easier.
```

---

## Practice 3: Return Value

Question:

```txt
If dummy node is used, should we return dummy or dummy.next?
```

Answer:

```txt
Return dummy.next.
```

Reason:

```txt
dummy is fake.
dummy.next points to the real result list.
```

---

## Practice 4: Remove All Target Values

Given:

```txt
head → 20 → 10 → 20 → 30 → null
target = 20
```

Output:

```txt
10 → 30 → null
```

Dummy setup:

```txt
dummy → 20 → 10 → 20 → 30 → null
```

Deletion rule:

```java
current.next = current.next.next;
```

---

## Practice 5: Remove Target Values at Head

Given:

```txt
head → 20 → 20 → 10 → 30 → null
target = 20
```

Output:

```txt
10 → 30 → null
```

Why dummy helps:

```txt
Both target nodes are at the beginning.
Dummy allows deleting them using the same current.next logic.
```

Dry run:

| Step | current | current.next | Action |
|---:|---|---|---|
| 1 | dummy | 20 | delete |
| 2 | dummy | 20 | delete |
| 3 | dummy | 10 | move |
| 4 | 10 | 30 | move |
| 5 | 30 | null | stop |

---

## Practice 6: Remove All Nodes

Given:

```txt
head → 7 → 7 → 7 → null
target = 7
```

Output:

```txt
null
```

Reason:

```txt
All nodes are removed.
dummy.next becomes null.
```

Return:

```java
return dummy.next;
```

---

## Practice 7: Target Not Present

Given:

```txt
head → 1 → 2 → 3 → null
target = 5
```

Output:

```txt
1 → 2 → 3 → null
```

Reason:

```txt
No node matches target.
List remains unchanged.
```

---

## Practice 8: Empty List

Given:

```txt
head → null
target = 10
```

Output:

```txt
null
```

Dummy setup:

```txt
dummy → null
```

Loop condition:

```java
while (current.next != null)
```

Since `current.next` is null, loop does not run.

---

## Practice 9: Delete First Target Only

Given:

```txt
head → 10 → 20 → 30 → 20 → null
target = 20
```

Output:

```txt
10 → 30 → 20 → null
```

Why only first target is removed?

```txt
Because we break after first deletion.
```

Code idea:

```java
if (current.next.val == target) {
    current.next = current.next.next;
    break;
}
```

---

## Practice 10: Delete First Target at Head

Given:

```txt
head → 10 → 20 → 30 → null
target = 10
```

Output:

```txt
20 → 30 → null
```

With dummy:

```txt
dummy → 10 → 20 → 30 → null
```

Delete:

```java
dummy.next = dummy.next.next;
```

Return:

```txt
dummy.next
```

---

## Practice 11: Remove Values Greater Than X

Given:

```txt
head → 5 → 12 → 3 → 20 → 8 → null
x = 10
```

Remove all values greater than `10`.

Output:

```txt
5 → 3 → 8 → null
```

Removed values:

```txt
12, 20
```

Pattern:

```txt
Dummy Node + Delete by Condition
```

---

## Practice 12: Keep Only Even Values

Given:

```txt
head → 1 → 2 → 3 → 4 → 5 → 6 → null
```

Output:

```txt
2 → 4 → 6 → null
```

Condition:

```txt
remove node if value is odd
```

Code condition:

```java
if (current.next.val % 2 != 0)
```

---

## Practice 13: Remove Negative Values

Given:

```txt
head → -1 → 5 → -3 → 7 → null
```

Output:

```txt
5 → 7 → null
```

Condition:

```txt
remove node if value < 0
```

---

## Practice 14: Insert Before Target

Given:

```txt
head → 10 → 20 → 30 → null
target = 20
value = 15
```

Output:

```txt
10 → 15 → 20 → 30 → null
```

Pointer setup when target found:

```txt
current = 10
current.next = 20
```

Insertion:

```java
newNode.next = current.next;
current.next = newNode;
```

---

## Practice 15: Insert Before Head Target

Given:

```txt
head → 10 → 20 → 30 → null
target = 10
value = 5
```

Output:

```txt
5 → 10 → 20 → 30 → null
```

Why dummy helps:

```txt
Target is at head.
Dummy acts as previous node before head.
```

---

## Practice 16: Insert Before Target Not Found

Given:

```txt
head → 10 → 20 → 30 → null
target = 50
value = 45
```

Output:

```txt
10 → 20 → 30 → null
```

Reason:

```txt
Target is not present, so no insertion happens.
```

---

## Practice 17: Build New Filtered List

Given:

```txt
head → 3 → 10 → 5 → 20 → null
x = 6
```

Build a new list containing values greater than 6.

Output:

```txt
10 → 20 → null
```

Use:

```txt
dummy
tail
current
```

---

## Practice 18: Dummy + Tail Dry Run

Input:

```txt
3 → 10 → 5 → 20 → null
x = 6
```

Initial:

```txt
dummy → null
tail = dummy
```

Dry run:

| current | Add to result? | tail after action | Result list |
|---:|---|---|---|
| 3 | No | dummy | empty |
| 10 | Yes | 10 | 10 |
| 5 | No | 10 | 10 |
| 20 | Yes | 20 | 10 → 20 |

Return:

```txt
dummy.next
```

Output:

```txt
10 → 20 → null
```

---

## Practice 19: Copy Full Linked List

Given:

```txt
head → 1 → 2 → 3 → null
```

Output copied list:

```txt
1 → 2 → 3 → null
```

Important:

```txt
New nodes should be created.
Original nodes should not be reused.
```

---

## Practice 20: Merge Two Sorted Lists

Given:

```txt
list1: 1 → 3 → 5 → null
list2: 2 → 4 → 6 → null
```

Output:

```txt
1 → 2 → 3 → 4 → 5 → 6 → null
```

Use:

```txt
dummy
tail
list1
list2
```

Pattern:

```txt
Dummy Node + Merge Pattern
```

---

## Practice 21: Merge When One List is Empty

Given:

```txt
list1: null
list2: 1 → 2 → 3 → null
```

Output:

```txt
1 → 2 → 3 → null
```

Reason:

```txt
If one list is empty, attach the other list.
```

---

## Practice 22: Remove Duplicates II Concept

Given sorted list:

```txt
1 → 2 → 3 → 3 → 4 → 4 → 5 → null
```

Remove all values that appear more than once.

Output:

```txt
1 → 2 → 5 → null
```

Why dummy helps:

```txt
If duplicates start at head, head may change.
```

Example:

```txt
1 → 1 → 2 → 3 → null
```

Output:

```txt
2 → 3 → null
```

---

## Practice 23: Partition List Concept

Given:

```txt
head → 1 → 4 → 3 → 2 → 5 → 2 → null
x = 3
```

Output:

```txt
1 → 2 → 2 → 4 → 3 → 5 → null
```

Use two dummy lists:

```txt
beforeDummy for values < x
afterDummy for values >= x
```

Final connection:

```java
beforeTail.next = afterDummy.next;
```

Important:

```java
afterTail.next = null;
```

This prevents accidental cycles.

---

## Practice 24: Identify the Bug

Wrong code:

```java
ListNode dummy = new ListNode(0);
ListNode current = dummy;

while (current.next != null) {
    current = current.next;
}

return dummy.next;
```

Question:

```txt
What is wrong?
```

Answer:

```txt
dummy.next was never connected to head.
```

Correct:

```java
ListNode dummy = new ListNode(0);
dummy.next = head;
ListNode current = dummy;
```

---

## Practice 25: Identify the Bug

Wrong code:

```java
return dummy;
```

Question:

```txt
Why is this wrong?
```

Answer:

```txt
dummy is a fake node.
Returning dummy includes the fake node in the result.
```

Correct:

```java
return dummy.next;
```

---

## Practice 26: Identify the Bug

Wrong code:

```java
if (current.next.val == target) {
    current.next = current.next.next;
    current = current.next;
}
```

Question:

```txt
Why can this be wrong while removing all target values?
```

Answer:

```txt
It moves current after deletion and may skip consecutive target nodes.
```

Correct:

```java
if (current.next.val == target) {
    current.next = current.next.next;
} else {
    current = current.next;
}
```

---

## Practice 27: Fill the Blank — Dummy Setup

Complete the code:

```java
ListNode dummy = new ListNode(0);
dummy.next = _____;

ListNode current = _____;
```

Answer:

```java
ListNode dummy = new ListNode(0);
dummy.next = head;

ListNode current = dummy;
```

---

## Practice 28: Fill the Blank — Delete current.next

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

## Practice 29: Fill the Blank — Build New List

Complete:

```java
tail.next = new ListNode(current.val);
tail = _____;
```

Answer:

```java
tail.next = new ListNode(current.val);
tail = tail.next;
```

---

## Practice 30: Fill the Blank — Return Result

If dummy node is used, return:

```java
return _____;
```

Answer:

```java
return dummy.next;
```

---

## Practice 31: MCQ Check

### Q1. What is a dummy node?

```txt
A. The last node of the list
B. A fake node before the real head
C. A node with maximum value
D. A node used only in arrays
```

Answer:

```txt
B. A fake node before the real head
```

---

### Q2. What should be returned when dummy is used?

```txt
A. dummy
B. dummy.next
C. head.next.next always
D. null always
```

Answer:

```txt
B. dummy.next
```

---

### Q3. When is dummy node useful?

```txt
A. Only for printing values
B. When head may change
C. Only for binary search
D. Only for arrays
```

Answer:

```txt
B. When head may change
```

---

### Q4. For deletion using dummy, which node is usually checked?

```txt
A. current.next
B. random
C. index
D. pivot
```

Answer:

```txt
A. current.next
```

---

### Q5. Why should current not always move after deletion?

```txt
A. It may skip consecutive nodes that also need deletion
B. It makes code O(1)
C. It sorts the list
D. It creates a new list automatically
```

Answer:

```txt
A. It may skip consecutive nodes that also need deletion
```

---

## Practice 32: Pattern Identification

Identify whether dummy node should be used.

| Problem | Use Dummy? | Reason |
|---|---|---|
| Print all nodes | No | Head does not change |
| Find length | No | Only traversal |
| Remove all target values | Yes | Head may change |
| Insert before target | Yes | Target may be head |
| Merge two sorted lists | Yes | Easier result construction |
| Search a value | No | No structural change |
| Delete duplicates II | Yes | First value may be removed |
| Partition list | Yes | Build two result lists |

---

## Practice 33: Complexity Check

Fill the complexity table:

| Operation | Time | Space |
|---|---:|---:|
| Remove all target values | O(n) | O(1) |
| Delete first target | O(n) | O(1) |
| Remove odd values | O(n) | O(1) |
| Insert before target | O(n) | O(1) |
| Build filtered copied list | O(n) | O(n) |
| Copy full list | O(n) | O(n) |
| Merge two sorted lists using existing nodes | O(n + m) | O(1) |

---

## Practice 34: Mini Coding Problem Set

Try writing code for these without looking at templates.

```txt
1. Remove all nodes with target value
2. Delete first node with target value
3. Remove all nodes greater than x
4. Remove all odd values
5. Keep only even values
6. Insert before first target
7. Insert before every target
8. Build a copied linked list
9. Build a filtered linked list
10. Merge two sorted linked lists
```

---

## Practice 35: Edge Case Checklist

Test dummy node solutions on:

```txt
head = null
head = 10 → null
target at head
target at tail
target in middle
target not present
all nodes match target
consecutive matching nodes
first few nodes match target
last few nodes match target
result list becomes empty
```

---

## Practice 36: Dummy Node Safety Checklist

Before submitting a dummy node solution, check:

```txt
Did I create dummy?
Did I connect dummy.next = head?
Did I start current from dummy for deletion?
Did I use current.next safely?
Did I avoid current.next.val when current.next is null?
Did I move current only when needed?
Did I return dummy.next?
Did I avoid returning dummy?
Did I test head-changing cases?
```

---

## Day 5 Final Revision

```txt
Dummy node is a fake node before head.

Use it when:
head may change
deletion starts from head
building a new result list
merging lists
inserting before head

Deletion:
current starts at dummy
check current.next
delete using current.next = current.next.next

Building:
tail starts at dummy
append using tail.next
move tail

Return:
dummy.next
```

---

## Day 5 Completion Checklist

| Task | Status |
|---|---|
| Understand dummy node | ✅ |
| Understand why dummy helps | ✅ |
| Use dummy for deletion | ✅ |
| Remove all target values | ✅ |
| Delete first target only | ✅ |
| Remove by condition | ✅ |
| Insert before target | ✅ |
| Build new list with dummy + tail | ✅ |
| Merge lists with dummy + tail | ✅ |
| Return dummy.next | ✅ |
| Avoid deletion skip bug | ✅ |
| Handle empty list | ✅ |
| Handle all-nodes-deleted case | ✅ |
| Understand complexity | ✅ |
