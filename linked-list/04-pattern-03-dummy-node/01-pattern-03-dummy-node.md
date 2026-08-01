# Pattern 03: Dummy Node / Sentinel Node

Dummy Node is one of the most useful linked list patterns.

It is used when the head of the linked list may change, especially during deletion, insertion, merging, or building a new list.

A dummy node is a temporary fake node placed before the actual head to simplify pointer handling.

---

## Why This Pattern Matters

In linked list problems, the head node is special.

If we delete, insert, or modify nodes near the beginning of the list, the head may change.

Without a dummy node, we often need separate logic for:

```txt
empty list
single node list
deleting head
deleting multiple head nodes
building a new list
merging lists
```

Dummy node reduces these special cases.

It helps us write cleaner, safer, and more consistent code.

---

## Pattern Name

```txt
Dummy Node / Sentinel Node
```

Also known as:

```txt
Sentinel node
Fake head
Temporary head
Pre-head node
Dummy head
```

---

## What is a Dummy Node?

A dummy node is an extra node created before the actual head.

Example:

```txt
Original list:

head → 10 → 20 → 30 → null
```

With dummy node:

```txt
dummy → 10 → 20 → 30 → null
         ↑
        head
```

In code:

```java
ListNode dummy = new ListNode(0);
dummy.next = head;
```

Here:

```txt
dummy is not part of the actual answer
dummy.next points to the real head
```

At the end, we return:

```java
return dummy.next;
```

---

## Why Return `dummy.next`?

The dummy node is fake.

The real linked list starts from:

```txt
dummy.next
```

So whenever we use a dummy node, the final return is usually:

```java
return dummy.next;
```

Example:

```txt
dummy → 10 → 20 → 30 → null
```

Returned list:

```txt
10 → 20 → 30 → null
```

---

## Pattern Signal

Use Dummy Node when the problem says:

```txt
delete nodes
remove elements
remove all target values
remove nth node
merge two lists
build a new linked list
insert before head
head may change
return modified head
handle deletion at beginning
```

Common problem statements:

```txt
Remove all nodes with value target.
Remove nth node from end.
Merge two sorted linked lists.
Delete duplicates from a sorted linked list.
Partition linked list.
Add two numbers represented by linked lists.
Swap nodes in pairs.
```

---

## Main Idea

Dummy node gives us a stable node before the head.

This means we can treat the head node the same way as any other node.

Without dummy:

```txt
head deletion needs separate handling
```

With dummy:

```txt
head deletion becomes normal deletion of dummy.next
```

---

## Basic Dummy Node Template

```java
class Solution {
    public ListNode solve(ListNode head) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;

        ListNode current = dummy;

        while (current.next != null) {
            // process current.next
            current = current.next;
        }

        return dummy.next;
    }
}
```

---

## Why `current` Starts From Dummy

If we want to delete or modify the node after `current`, we need a previous node.

For the original head, there is no previous node.

Dummy solves this.

```txt
dummy → head → nextNode
```

Now dummy acts as the previous node of head.

So deleting head becomes:

```java
dummy.next = dummy.next.next;
```

This is the same as deleting any other next node.

---

## Problem Without Dummy Node

Suppose we want to remove all nodes with value `20`.

Input:

```txt
head → 20 → 20 → 10 → 20 → 30 → null
```

Expected output:

```txt
head → 10 → 30 → null
```

Without dummy, we need special handling for head:

```java
while (head != null && head.val == target) {
    head = head.next;
}
```

Then we handle the remaining nodes.

This works, but the code becomes more complicated.

---

## Same Problem With Dummy Node

Input:

```txt
head → 20 → 20 → 10 → 20 → 30 → null
```

Add dummy:

```txt
dummy → 20 → 20 → 10 → 20 → 30 → null
```

Now we can check:

```txt
current.next
```

If `current.next.val == target`, delete `current.next`.

This also handles target nodes at the beginning.

---

## Operation 1: Remove All Nodes With Target Value

Problem:

```txt
Given the head of a linked list and an integer target, remove all nodes whose value is equal to target.
```

Example:

```txt
Input:
20 → 20 → 10 → 20 → 30 → null

target = 20

Output:
10 → 30 → null
```

---

## Logic

```txt
1. Create dummy node.
2. Connect dummy.next to head.
3. Start current from dummy.
4. Check current.next.
5. If current.next value is target, skip current.next.
6. Otherwise move current forward.
7. Return dummy.next.
```

---

## Java Code

```java
class Solution {
    public ListNode removeElements(ListNode head, int target) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;

        ListNode current = dummy;

        while (current.next != null) {
            if (current.next.val == target) {
                current.next = current.next.next;
            } else {
                current = current.next;
            }
        }

        return dummy.next;
    }
}
```

---

## Why We Check `current.next`

We check:

```java
current.next.val
```

instead of:

```java
current.val
```

because deletion needs access to the previous node.

To delete a node, we need to change the previous node's `next`.

```txt
current → nodeToDelete → nextNode
```

Deletion:

```java
current.next = current.next.next;
```

---

## Remove Elements Dry Run

Input:

```txt
20 → 20 → 10 → 20 → 30 → null
target = 20
```

With dummy:

```txt
dummy → 20 → 20 → 10 → 20 → 30 → null
```

Initial:

```txt
current = dummy
```

Dry run:

| Step | current | current.next | Action | List after action |
|---:|---|---|---|---|
| 1 | dummy | 20 | delete current.next | dummy → 20 → 10 → 20 → 30 |
| 2 | dummy | 20 | delete current.next | dummy → 10 → 20 → 30 |
| 3 | dummy | 10 | move current | dummy → 10 → 20 → 30 |
| 4 | 10 | 20 | delete current.next | dummy → 10 → 30 |
| 5 | 10 | 30 | move current | dummy → 10 → 30 |
| 6 | 30 | null | stop | final |

Return:

```java
dummy.next
```

Output:

```txt
10 → 30 → null
```

---

## Most Important Rule in Deletion

When deletion happens:

```java
current.next = current.next.next;
```

Do not move current immediately.

Why?

Because the new `current.next` may also need deletion.

Example:

```txt
20 → 20 → 20 → 10 → null
```

If we move current after deleting one `20`, we may skip the next `20`.

Correct:

```java
if (current.next.val == target) {
    current.next = current.next.next;
} else {
    current = current.next;
}
```

---

## Operation 2: Delete First Node With Target Value

Problem:

```txt
Delete only the first node whose value equals target.
```

Example:

```txt
Input:
10 → 20 → 30 → 20 → null

target = 20

Output:
10 → 30 → 20 → null
```

Code:

```java
class Solution {
    public ListNode deleteFirstTarget(ListNode head, int target) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;

        ListNode current = dummy;

        while (current.next != null) {
            if (current.next.val == target) {
                current.next = current.next.next;
                break;
            }

            current = current.next;
        }

        return dummy.next;
    }
}
```

---

## Delete First Target Dry Run

Input:

```txt
10 → 20 → 30 → 20 → null
target = 20
```

With dummy:

```txt
dummy → 10 → 20 → 30 → 20 → null
```

Steps:

```txt
current = dummy
current.next = 10 → not target → move
current = 10
current.next = 20 → target found
```

Delete:

```java
current.next = current.next.next;
```

Meaning:

```txt
10.next = 30
```

Result:

```txt
10 → 30 → 20 → null
```

---

## Operation 3: Remove Nodes Greater Than a Value

Problem:

```txt
Remove all nodes whose value is greater than x.
```

Example:

```txt
Input:
5 → 12 → 3 → 20 → 8 → null

x = 10

Output:
5 → 3 → 8 → null
```

Code:

```java
class Solution {
    public ListNode removeGreaterThanX(ListNode head, int x) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;

        ListNode current = dummy;

        while (current.next != null) {
            if (current.next.val > x) {
                current.next = current.next.next;
            } else {
                current = current.next;
            }
        }

        return dummy.next;
    }
}
```

This uses the same dummy deletion pattern.

---

## Operation 4: Keep Only Even Values

Problem:

```txt
Remove all odd-valued nodes and keep only even values.
```

Example:

```txt
Input:
1 → 2 → 3 → 4 → 5 → 6 → null

Output:
2 → 4 → 6 → null
```

Code:

```java
class Solution {
    public ListNode keepEvenValues(ListNode head) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;

        ListNode current = dummy;

        while (current.next != null) {
            if (current.next.val % 2 != 0) {
                current.next = current.next.next;
            } else {
                current = current.next;
            }
        }

        return dummy.next;
    }
}
```

---

## Operation 5: Build a New List Using Dummy Node

Dummy node is not only used for deletion.

It is also used for building a new linked list.

Example:

```txt
Create a new list containing only values greater than x.
```

Input:

```txt
3 → 10 → 5 → 20 → null
x = 6
```

Output:

```txt
10 → 20 → null
```

---

## Dummy + Tail Technique

When building a new list, we usually use:

```txt
dummy
tail
```

```java
ListNode dummy = new ListNode(0);
ListNode tail = dummy;
```

Meaning:

```txt
dummy marks the fake beginning
tail tracks the last node of the new list
```

When adding a node:

```java
tail.next = new ListNode(value);
tail = tail.next;
```

At the end:

```java
return dummy.next;
```

---

## Build New List Code

```java
class Solution {
    public ListNode filterGreaterThanX(ListNode head, int x) {
        ListNode dummy = new ListNode(0);
        ListNode tail = dummy;

        ListNode current = head;

        while (current != null) {
            if (current.val > x) {
                tail.next = new ListNode(current.val);
                tail = tail.next;
            }

            current = current.next;
        }

        return dummy.next;
    }
}
```

---

## Build New List Dry Run

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

Process:

| current | Is current > 6? | Action | New list |
|---:|---|---|---|
| 3 | No | skip | dummy |
| 10 | Yes | add 10 | dummy → 10 |
| 5 | No | skip | dummy → 10 |
| 20 | Yes | add 20 | dummy → 10 → 20 |

Return:

```txt
dummy.next
```

Output:

```txt
10 → 20 → null
```

---

## Operation 6: Merge Two Sorted Lists Using Dummy Node

Problem:

```txt
Given two sorted linked lists, merge them into one sorted linked list.
```

Example:

```txt
list1: 1 → 3 → 5 → null
list2: 2 → 4 → 6 → null

Output:
1 → 2 → 3 → 4 → 5 → 6 → null
```

This is mainly a merge pattern, but dummy node is used to build the result cleanly.

---

## Code

```java
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode dummy = new ListNode(0);
        ListNode tail = dummy;

        while (list1 != null && list2 != null) {
            if (list1.val <= list2.val) {
                tail.next = list1;
                list1 = list1.next;
            } else {
                tail.next = list2;
                list2 = list2.next;
            }

            tail = tail.next;
        }

        if (list1 != null) {
            tail.next = list1;
        } else {
            tail.next = list2;
        }

        return dummy.next;
    }
}
```

---

## Why Dummy Helps in Merge

Without dummy, we need to decide the first node of the result separately.

With dummy:

```txt
dummy → result starts here
tail keeps moving
```

We do not need special logic for the first node.

---

## Operation 7: Insert Before First Target

Problem:

```txt
Insert a new node before the first node whose value equals target.
```

Example:

```txt
Input:
10 → 20 → 30 → null

target = 20
value = 15

Output:
10 → 15 → 20 → 30 → null
```

This is a perfect dummy node problem because target may be at head.

Example:

```txt
target = 10
value = 5
```

Output:

```txt
5 → 10 → 20 → 30 → null
```

---

## Code

```java
class Solution {
    public ListNode insertBeforeTarget(ListNode head, int target, int value) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;

        ListNode current = dummy;

        while (current.next != null) {
            if (current.next.val == target) {
                ListNode newNode = new ListNode(value);

                newNode.next = current.next;
                current.next = newNode;

                break;
            }

            current = current.next;
        }

        return dummy.next;
    }
}
```

---

## Insert Before Target Dry Run

Input:

```txt
10 → 20 → 30 → null
target = 10
value = 5
```

With dummy:

```txt
dummy → 10 → 20 → 30 → null
```

Initial:

```txt
current = dummy
current.next = 10
```

Target found.

Insert:

```java
newNode.next = current.next;
current.next = newNode;
```

Result:

```txt
dummy → 5 → 10 → 20 → 30 → null
```

Return:

```txt
dummy.next
```

Output:

```txt
5 → 10 → 20 → 30 → null
```

---

## Dummy Node vs Normal Pointer Rewiring

| Situation | Without Dummy | With Dummy |
|---|---|---|
| Delete head | Special case needed | Same as normal deletion |
| Delete multiple head nodes | Extra loop needed | Simple loop |
| Build new list | Need first-node handling | Use dummy + tail |
| Merge lists | Need result head setup | Use dummy + tail |
| Insert before head | Special case needed | Same as normal insertion |
| Return result | Return head carefully | Return dummy.next |

---

## When Dummy Node is Best

Use dummy node when:

```txt
head may change
first node may be deleted
multiple starting nodes may be deleted
new list is being built
two lists are being merged
insertion may happen before head
deletion conditions are repeated
```

---

## When Dummy Node is Not Required

Dummy node is usually not needed when:

```txt
only traversing
only searching
only counting length
only finding max/min
only checking if value exists
```

For these, simple `current` traversal is enough.

---

## Pattern Recognition Summary

Use Dummy Node when you see:

```txt
remove all
delete nodes
insert before
merge lists
build result list
head may change
return modified head
```

Main template:

```java
ListNode dummy = new ListNode(0);
dummy.next = head;
ListNode current = dummy;
```

Final return:

```java
return dummy.next;
```

---

## Common Mistakes

| Mistake | Why it is wrong | Correct thinking |
|---|---|---|
| Returning `dummy` | Dummy is fake | Return `dummy.next` |
| Moving current after deletion | Can skip consecutive nodes | Move only when no deletion |
| Checking `current.val` for deletion | Cannot delete current easily | Check `current.next` |
| Forgetting `dummy.next = head` | Original list is disconnected | Always connect dummy to head |
| Creating dummy but returning old head | Head changes are ignored | Return `dummy.next` |
| Not using tail while building new list | Hard to append nodes | Use dummy + tail |

---

## Mistake Example 1: Returning Dummy

Wrong:

```java
return dummy;
```

Problem:

```txt
This returns the fake node also.
```

Correct:

```java
return dummy.next;
```

---

## Mistake Example 2: Moving Current After Deletion

Wrong:

```java
if (current.next.val == target) {
    current.next = current.next.next;
}

current = current.next;
```

Problem:

```txt
This can skip consecutive target nodes.
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

## Mistake Example 3: Forgetting to Connect Dummy

Wrong:

```java
ListNode dummy = new ListNode(0);
ListNode current = dummy;
```

Problem:

```txt
dummy is not connected to head.
The original list is ignored.
```

Correct:

```java
ListNode dummy = new ListNode(0);
dummy.next = head;
ListNode current = dummy;
```

---

## Complexity

For most dummy node deletion problems:

```txt
Time Complexity: O(n)
Space Complexity: O(1)
```

Why?

```txt
We visit each node at most once.
We only use dummy and current pointers.
```

For building a new list:

```txt
Time Complexity: O(n)
Space Complexity: O(n)
```

Why?

```txt
We create new nodes for the result list.
```

For merging two lists using existing nodes:

```txt
Time Complexity: O(n + m)
Space Complexity: O(1)
```

where:

```txt
n = length of first list
m = length of second list
```

---

## Complexity Summary

| Operation | Time | Space |
|---|---:|---:|
| Remove all target values | O(n) | O(1) |
| Delete first target | O(n) | O(1) |
| Remove values greater than x | O(n) | O(1) |
| Keep only even values | O(n) | O(1) |
| Build new filtered list | O(n) | O(n) |
| Merge two sorted lists using existing nodes | O(n + m) | O(1) |
| Insert before target | O(n) | O(1) |

---

## Day 5 Learning Goal

After completing this pattern, you should be able to:

```txt
understand what dummy node is
know why dummy node is used
handle head-changing cases
delete nodes safely
remove all target values
insert before target
build new linked list using dummy and tail
merge two lists using dummy and tail
return dummy.next correctly
avoid common dummy node mistakes
```

---

## Final Revision

```txt
Dummy node = fake node before head

Create:
ListNode dummy = new ListNode(0);
dummy.next = head;

Use:
current = dummy

Delete current.next:
current.next = current.next.next

Build result:
tail.next = newNode
tail = tail.next

Return:
dummy.next
```

---

## Final Checklist

| Skill | Status |
|---|---|
| Understand dummy node | ✅ |
| Understand sentinel node idea | ✅ |
| Know when head can change | ✅ |
| Remove all target values | ✅ |
| Delete first target | ✅ |
| Remove by condition | ✅ |
| Insert before target | ✅ |
| Build new list using dummy + tail | ✅ |
| Merge using dummy + tail | ✅ |
| Return dummy.next | ✅ |
| Avoid skipping nodes after deletion | ✅ |
| Understand complexity | ✅ |
