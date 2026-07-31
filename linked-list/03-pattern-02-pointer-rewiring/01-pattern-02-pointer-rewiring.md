# Pattern 02: Pointer Rewiring, Insertion, Deletion and Swapping

Pointer Rewiring is one of the most important linked list patterns.

In Day 3, we learned how to move through a linked list using traversal.

In Day 4, we learn how to change the structure of the linked list by modifying links.

This pattern is used when we need to:

```txt
insert a node
delete a node
skip a node
connect nodes differently
swap nodes
modify next references
return an updated linked list
```

---

## Why This Pattern Matters

Linked List problems are mostly about references.

The real power of linked list comes from changing node connections.

In arrays, insertion and deletion usually require shifting elements.

In linked list, insertion and deletion are done by changing `next` references.

Example:

```txt
10 → 20 → 30 → null
```

If we want to delete `20`, we do not shift values.

We change the link:

```txt
10.next = 30
```

Result:

```txt
10 → 30 → null
```

This is called pointer rewiring.

---

## Pattern Name

```txt
Pointer Rewiring
```

Also known as:

```txt
Link manipulation
Node connection change
Reference update
Next pointer modification
```

---

## Pattern Goal

The goal of this pattern is to safely change node connections without losing access to the remaining linked list.

Whenever you write:

```java
someNode.next = anotherNode;
```

you are rewiring pointers.

---

## Basic Linked List Structure

```txt
head → 10 → 20 → 30 → 40 → null
```

Each arrow represents a `next` reference.

```txt
10.next = 20
20.next = 30
30.next = 40
40.next = null
```

Pointer rewiring means changing one or more of these connections.

---

## Pattern Signal

Use this pattern when the problem says:

```txt
insert a node
delete a node
remove a node
remove elements
skip nodes
swap nodes
change links
modify linked list
return updated list
delete node by value
insert after a value
remove duplicates
```

Common problem statements:

```txt
Insert a node at the beginning of a linked list.
Insert a node at the end of a linked list.
Delete a node with a given value.
Delete the last node.
Remove all nodes with a given value.
Swap two adjacent nodes.
Remove duplicates from a sorted linked list.
```

---

## Main Pointers Used

This pattern commonly uses:

```txt
current
previous
nextNode
head
```

| Pointer | Purpose |
|---|---|
| `current` | Node currently being checked |
| `previous` | Node before current |
| `nextNode` | Saves next node before changing links |
| `head` | Starting node of list |

---

## Why `previous` is Important

To delete a node, we usually need the node before it.

Example:

```txt
10 → 20 → 30 → null
```

To delete `20`, we need access to `10`.

Then:

```java
previous.next = current.next;
```

If:

```txt
previous = 10
current = 20
current.next = 30
```

Then:

```txt
previous.next = current.next
10.next = 30
```

Result:

```txt
10 → 30 → null
```

---

## Why `nextNode` is Important

Sometimes, before changing `current.next`, we must save the original next node.

Example:

```java
ListNode nextNode = current.next;
current.next = previous;
```

This is very important in reversal and swapping.

If we change `current.next` without saving the next node, we may lose access to the remaining list.

---

## Safe Rewiring Rule

Before changing any link:

```java
current.next = something;
```

always ask:

```txt
Will I lose access to the next node?
Should I save current.next first?
Can head change?
Can current become null?
What should be returned?
```

This rule prevents most linked list bugs.

---

## Operation 1: Insert at Head

Problem:

```txt
Insert a new node at the beginning of the linked list.
```

Before:

```txt
head → 10 → 20 → 30 → null
```

Insert:

```txt
5
```

Step 1:

```txt
newNode → 5 → null
```

Step 2:

```java
newNode.next = head;
```

Now:

```txt
newNode → 5 → 10 → 20 → 30 → null
```

Step 3:

```java
head = newNode;
```

After:

```txt
head → 5 → 10 → 20 → 30 → null
```

Code:

```java
class Solution {
    public ListNode insertAtHead(ListNode head, int value) {
        ListNode newNode = new ListNode(value);
        newNode.next = head;
        head = newNode;

        return head;
    }
}
```

Time complexity:

```txt
O(1)
```

Space complexity:

```txt
O(1)
```

---

## Insert at Head Dry Run

Input:

```txt
head → 10 → 20 → null
value = 5
```

Initial:

```txt
newNode → 5 → null
```

After:

```java
newNode.next = head;
```

```txt
5 → 10 → 20 → null
```

After:

```java
head = newNode;
```

```txt
head → 5 → 10 → 20 → null
```

Return:

```txt
head
```

---

## Operation 2: Insert at Tail

Problem:

```txt
Insert a new node at the end of the linked list.
```

Before:

```txt
head → 10 → 20 → 30 → null
```

Insert:

```txt
40
```

After:

```txt
head → 10 → 20 → 30 → 40 → null
```

Logic:

```txt
If head is null, new node becomes head.
Otherwise, move to the last node.
Connect last node to new node.
```

Code:

```java
class Solution {
    public ListNode insertAtTail(ListNode head, int value) {
        ListNode newNode = new ListNode(value);

        if (head == null) {
            return newNode;
        }

        ListNode current = head;

        while (current.next != null) {
            current = current.next;
        }

        current.next = newNode;

        return head;
    }
}
```

---

## Why Loop Uses `current.next != null`

For tail insertion, we want to stop at the last node.

The last node is the node whose `next` is `null`.

So we use:

```java
while (current.next != null)
```

If we use:

```java
while (current != null)
```

then current will become `null`, and we cannot connect the new node.

---

## Insert at Tail Dry Run

Input:

```txt
head → 10 → 20 → 30 → null
value = 40
```

Start:

```txt
current = 10
```

Loop:

| Step | current | current.next |
|---:|---:|---|
| 1 | 10 | 20 |
| 2 | 20 | 30 |
| 3 | 30 | null |

Stop at:

```txt
current = 30
```

Then:

```java
current.next = newNode;
```

Result:

```txt
10 → 20 → 30 → 40 → null
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

## Operation 3: Insert After a Given Value

Problem:

```txt
Insert a new node after the first node with target value.
```

Before:

```txt
head → 10 → 20 → 30 → null
```

Insert `25` after `20`.

After:

```txt
head → 10 → 20 → 25 → 30 → null
```

Logic:

```txt
Search target node.
Create new node.
Connect newNode.next to current.next.
Connect current.next to newNode.
```

Important order:

```java
newNode.next = current.next;
current.next = newNode;
```

If we reverse the order, we may lose the remaining list.

Code:

```java
class Solution {
    public ListNode insertAfterValue(ListNode head, int target, int value) {
        ListNode current = head;

        while (current != null) {
            if (current.val == target) {
                ListNode newNode = new ListNode(value);

                newNode.next = current.next;
                current.next = newNode;

                return head;
            }

            current = current.next;
        }

        return head;
    }
}
```

---

## Insert After Value Dry Run

Input:

```txt
head → 10 → 20 → 30 → null
target = 20
value = 25
```

When:

```txt
current = 20
```

Before insertion:

```txt
20 → 30
```

Step 1:

```java
newNode.next = current.next;
```

```txt
25 → 30
```

Step 2:

```java
current.next = newNode;
```

```txt
20 → 25 → 30
```

Final:

```txt
10 → 20 → 25 → 30 → null
```

---

## Operation 4: Delete Head

Problem:

```txt
Delete the first node of the linked list.
```

Before:

```txt
head → 10 → 20 → 30 → null
```

After:

```txt
head → 20 → 30 → null
```

Code:

```java
class Solution {
    public ListNode deleteHead(ListNode head) {
        if (head == null) {
            return null;
        }

        head = head.next;

        return head;
    }
}
```

Time complexity:

```txt
O(1)
```

Space complexity:

```txt
O(1)
```

---

## Delete Head Dry Run

Input:

```txt
head → 10 → 20 → 30 → null
```

Step:

```java
head = head.next;
```

Now:

```txt
head → 20 → 30 → null
```

The old first node `10` is no longer part of the list.

---

## Operation 5: Delete Tail

Problem:

```txt
Delete the last node of the linked list.
```

Before:

```txt
head → 10 → 20 → 30 → null
```

After:

```txt
head → 10 → 20 → null
```

Cases:

```txt
empty list
single node list
multiple node list
```

Code:

```java
class Solution {
    public ListNode deleteTail(ListNode head) {
        if (head == null) {
            return null;
        }

        if (head.next == null) {
            return null;
        }

        ListNode current = head;

        while (current.next.next != null) {
            current = current.next;
        }

        current.next = null;

        return head;
    }
}
```

---

## Why Use `current.next.next != null`

To delete the tail, we need to stop at the second last node.

Example:

```txt
10 → 20 → 30 → null
```

The second last node is:

```txt
20
```

Then:

```java
current.next = null;
```

This removes `30`.

---

## Delete Tail Dry Run

Input:

```txt
head → 10 → 20 → 30 → null
```

Start:

```txt
current = 10
```

Check:

```txt
current.next.next = 30
```

Move:

```txt
current = 20
```

Now:

```txt
current.next = 30
current.next.next = null
```

Stop.

Then:

```java
current.next = null;
```

Result:

```txt
10 → 20 → null
```

---

## Operation 6: Delete First Node With Given Value

Problem:

```txt
Delete the first node whose value equals target.
```

Before:

```txt
head → 10 → 20 → 30 → 20 → null
target = 20
```

After:

```txt
head → 10 → 30 → 20 → null
```

Logic:

```txt
If head is target, move head.
Otherwise, use previous and current.
Find target.
Connect previous.next to current.next.
```

Code:

```java
class Solution {
    public ListNode deleteFirstValue(ListNode head, int target) {
        if (head == null) {
            return null;
        }

        if (head.val == target) {
            return head.next;
        }

        ListNode previous = head;
        ListNode current = head.next;

        while (current != null) {
            if (current.val == target) {
                previous.next = current.next;
                return head;
            }

            previous = current;
            current = current.next;
        }

        return head;
    }
}
```

---

## Delete First Value Dry Run

Input:

```txt
head → 10 → 20 → 30 → null
target = 20
```

Initial:

```txt
previous = 10
current = 20
```

Since:

```txt
current.val == target
```

Do:

```java
previous.next = current.next;
```

Meaning:

```txt
10.next = 30
```

Result:

```txt
10 → 30 → null
```

---

## Operation 7: Delete All Nodes With Given Value

Problem:

```txt
Delete all nodes whose value equals target.
```

Before:

```txt
head → 20 → 20 → 10 → 20 → 30 → null
target = 20
```

After:

```txt
head → 10 → 30 → null
```

This is harder because multiple head nodes may also need deletion.

Code without dummy node:

```java
class Solution {
    public ListNode deleteAllValues(ListNode head, int target) {
        while (head != null && head.val == target) {
            head = head.next;
        }

        ListNode current = head;

        while (current != null && current.next != null) {
            if (current.next.val == target) {
                current.next = current.next.next;
            } else {
                current = current.next;
            }
        }

        return head;
    }
}
```

Note:

```txt
Dummy node makes this cleaner.
Dummy node will be covered in the next pattern.
```

---

## Delete All Values Dry Run

Input:

```txt
20 → 20 → 10 → 20 → 30 → null
target = 20
```

First remove target from head:

```txt
20 removed
20 removed
head → 10 → 20 → 30 → null
```

Now:

```txt
current = 10
```

Check:

```txt
current.next = 20
```

Since `20` is target:

```java
current.next = current.next.next;
```

Now:

```txt
10 → 30 → null
```

Final:

```txt
10 → 30 → null
```

---

## Operation 8: Insert at Position

Problem:

```txt
Insert a value at a given 0-based position.
```

Example:

```txt
head → 10 → 20 → 30 → null
position = 1
value = 15
```

After:

```txt
head → 10 → 15 → 20 → 30 → null
```

Code:

```java
class Solution {
    public ListNode insertAtPosition(ListNode head, int position, int value) {
        ListNode newNode = new ListNode(value);

        if (position == 0) {
            newNode.next = head;
            return newNode;
        }

        ListNode current = head;
        int index = 0;

        while (current != null && index < position - 1) {
            current = current.next;
            index++;
        }

        if (current == null) {
            return head;
        }

        newNode.next = current.next;
        current.next = newNode;

        return head;
    }
}
```

---

## Insert at Position Dry Run

Input:

```txt
10 → 20 → 30 → null
position = 1
value = 15
```

We need to stop at:

```txt
position - 1 = 0
```

So:

```txt
current = 10
```

Then:

```java
newNode.next = current.next;
current.next = newNode;
```

Result:

```txt
10 → 15 → 20 → 30 → null
```

---

## Operation 9: Delete at Position

Problem:

```txt
Delete node at a given 0-based position.
```

Example:

```txt
head → 10 → 20 → 30 → 40 → null
position = 2
```

After:

```txt
head → 10 → 20 → 40 → null
```

Code:

```java
class Solution {
    public ListNode deleteAtPosition(ListNode head, int position) {
        if (head == null) {
            return null;
        }

        if (position == 0) {
            return head.next;
        }

        ListNode current = head;
        int index = 0;

        while (current != null && current.next != null && index < position - 1) {
            current = current.next;
            index++;
        }

        if (current == null || current.next == null) {
            return head;
        }

        current.next = current.next.next;

        return head;
    }
}
```

---

## Delete at Position Dry Run

Input:

```txt
10 → 20 → 30 → 40 → null
position = 2
```

We need to stop at:

```txt
position - 1 = 1
```

So:

```txt
current = 20
```

Then:

```java
current.next = current.next.next;
```

Meaning:

```txt
20.next = 40
```

Result:

```txt
10 → 20 → 40 → null
```

---

## Operation 10: Swap First Two Nodes

Problem:

```txt
Swap the first two nodes of a linked list.
```

Before:

```txt
head → 10 → 20 → 30 → null
```

After:

```txt
head → 20 → 10 → 30 → null
```

Important:

```txt
We are swapping nodes, not values.
```

Code:

```java
class Solution {
    public ListNode swapFirstTwoNodes(ListNode head) {
        if (head == null || head.next == null) {
            return head;
        }

        ListNode first = head;
        ListNode second = head.next;
        ListNode third = second.next;

        second.next = first;
        first.next = third;

        return second;
    }
}
```

---

## Swap First Two Nodes Dry Run

Input:

```txt
head → 10 → 20 → 30 → null
```

Pointers:

```txt
first = 10
second = 20
third = 30
```

Step 1:

```java
second.next = first;
```

```txt
20 → 10
```

Step 2:

```java
first.next = third;
```

```txt
10 → 30
```

New head:

```txt
20
```

Final:

```txt
head → 20 → 10 → 30 → null
```

---

## Operation 11: Swap Two Adjacent Nodes After Previous

This is useful for pair swapping and local rewiring.

Before:

```txt
previous → first → second → nextNode
```

After:

```txt
previous → second → first → nextNode
```

Pointer setup:

```java
ListNode first = previous.next;
ListNode second = first.next;
ListNode nextNode = second.next;
```

Rewiring:

```java
previous.next = second;
second.next = first;
first.next = nextNode;
```

This pattern appears in:

```txt
swap nodes in pairs
reverse nodes in groups
local node swapping
```

---

## Node Swap vs Value Swap

Wrong shortcut:

```java
int temp = first.val;
first.val = second.val;
second.val = temp;
```

This swaps values, not nodes.

In many interview problems, changing values is not allowed.

Correct linked list thinking:

```txt
Change node links, not node values.
```

Pointer rewiring means changing `next` references.

---

## Head Change Cases

Head can change in:

```txt
insert at head
delete head
delete value if target is at head
delete position 0
swap first two nodes
reverse list
```

If head can change, return the updated head.

Examples:

```java
return newNode;
return head.next;
return second;
```

---

## When Pointer Rewiring Is Enough

Pointer Rewiring is enough when the problem asks for simple structural changes:

```txt
insert
delete
skip
swap nearby nodes
remove first match
remove all matches
```

Pointer Rewiring may need other patterns when the problem asks:

```txt
remove nth from end
reverse complete list
reverse k-group
merge lists
detect cycle
check palindrome
```

Those problems combine rewiring with other patterns.

---

## Common Mistakes

| Mistake | Why it is wrong | Correct approach |
|---|---|---|
| Forgetting head can change | Returns old list | Return updated head |
| Not saving next before rewiring | Loses remaining list | Store `nextNode` |
| Moving current after deletion incorrectly | Skips nodes | Move only when no deletion |
| Using `current.next.next` without check | NullPointerException | Check `current.next != null` |
| Swapping values instead of nodes | Not real rewiring | Change links |
| Deleting only first head match | Multiple head targets remain | Use while for head targets |

---

## Rewiring Mistake Example

Wrong insertion order:

```java
current.next = newNode;
newNode.next = current.next;
```

Problem:

```txt
newNode.next points to itself or wrong node.
Original next node may be lost.
```

Correct:

```java
newNode.next = current.next;
current.next = newNode;
```

Always connect the new node to the remaining list first.

---

## Deletion Mistake Example

Wrong:

```java
if (current.next.val == target) {
    current.next = current.next.next;
}
current = current.next;
```

Problem:

```txt
If there are consecutive target nodes, this may skip checking one node.
```

Better:

```java
if (current.next.val == target) {
    current.next = current.next.next;
} else {
    current = current.next;
}
```

Move only when no deletion happened.

---

## Pattern Complexity

Most pointer rewiring operations have:

```txt
Time Complexity: O(n)
Space Complexity: O(1)
```

Why O(n)?

```txt
Because we may need to search or traverse nodes.
```

Why O(1) space?

```txt
Because we only use a few pointers.
```

Operations like insert at head or delete head are:

```txt
Time Complexity: O(1)
Space Complexity: O(1)
```

---

## Complexity Summary

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

## Pattern Recognition Summary

Use Pattern 02 when the task says:

```txt
insert
delete
remove
skip
swap
connect
unlink
change next
modify list
```

Main idea:

```txt
Change next references safely.
```

Main pointers:

```txt
previous
current
nextNode
```

Main warning:

```txt
Do not lose the rest of the list.
```

---

## Day 4 Learning Goal

After completing this pattern, you should be able to:

```txt
insert at head
insert at tail
insert after a value
insert at a position
delete head
delete tail
delete first target value
delete all target values
delete at a position
swap first two nodes
understand node swap vs value swap
avoid losing links
handle head changes
```

---

## Final Revision

```txt
Pointer Rewiring = changing next references

Insert:
newNode.next = current.next
current.next = newNode

Delete:
previous.next = current.next

Delete next:
current.next = current.next.next

Swap first two:
second.next = first
first.next = third
return second

Safe rule:
Save next before changing links if needed.
```

---

## Final Checklist

| Skill | Status |
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
| Understand head change | ✅ |
| Avoid broken links | ✅ |
| Understand complexity | ✅ |
