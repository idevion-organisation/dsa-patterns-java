# Pointer Rewiring Templates in Java

This file contains reusable Java templates for Pattern 02.

Pointer Rewiring is used when a linked list problem asks us to modify node connections.

Use these templates when the problem involves:

```txt
insertion
deletion
removal
skipping nodes
swapping nodes
changing next pointers
returning modified head
```

---

## Basic ListNode Class

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

## Template 1: Insert at Head

Use when the problem asks:

```txt
insert at beginning
add node before current head
prepend node
```

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

Complexity:

```txt
Time Complexity: O(1)
Space Complexity: O(1)
```

---

## Template 2: Insert at Tail

Use when the problem asks:

```txt
insert at end
append node
add node after last node
```

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

Key condition:

```java
while (current.next != null)
```

This stops at the last node.

---

## Template 3: Insert After a Given Node

Use when the node reference is already given.

```java
class Solution {
    public void insertAfterNode(ListNode node, int value) {
        if (node == null) {
            return;
        }

        ListNode newNode = new ListNode(value);

        newNode.next = node.next;
        node.next = newNode;
    }
}
```

Complexity:

```txt
Time Complexity: O(1)
Space Complexity: O(1)
```

Important:

```txt
This is O(1) because the node is already given.
```

---

## Template 4: Insert After a Given Value

Use when the problem asks to insert after the first matching value.

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

Complexity:

```txt
Time Complexity: O(n)
Space Complexity: O(1)
```

Why O(n)?

```txt
Because target value may be at the end or may not exist.
```

---

## Template 5: Insert at Position

Use 0-based position.

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

Return unchanged list if position is invalid.

---

## Template 6: Delete Head

Use when the first node needs to be removed.

```java
class Solution {
    public ListNode deleteHead(ListNode head) {
        if (head == null) {
            return null;
        }

        return head.next;
    }
}
```

Complexity:

```txt
Time Complexity: O(1)
Space Complexity: O(1)
```

---

## Template 7: Delete Tail

Use when the last node needs to be removed.

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

Key idea:

```txt
Stop at second last node.
Set secondLast.next = null.
```

---

## Template 8: Delete First Value

Use when the first node with target value should be removed.

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

Used when:

```txt
only first matching node should be deleted
```

---

## Template 9: Delete All Values Without Dummy Node

Use when all nodes with target value should be removed.

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

Important:

```txt
Do not move current after deletion.
```

Why?

```txt
There may be consecutive target nodes.
```

---

## Template 10: Delete at Position

Use 0-based position.

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

## Template 11: Delete Next Node

Use when you are already at the node before the node to delete.

Before:

```txt
current → nodeToDelete → nextNode
```

After:

```txt
current → nextNode
```

Code:

```java
class Solution {
    public void deleteNextNode(ListNode current) {
        if (current == null || current.next == null) {
            return;
        }

        current.next = current.next.next;
    }
}
```

Complexity:

```txt
Time Complexity: O(1)
Space Complexity: O(1)
```

---

## Template 12: Remove Duplicates From Sorted List

Problem type:

```txt
sorted linked list
remove duplicate values
keep one occurrence
```

Example:

```txt
1 → 1 → 2 → 3 → 3 → null
```

After:

```txt
1 → 2 → 3 → null
```

Code:

```java
class Solution {
    public ListNode removeDuplicates(ListNode head) {
        ListNode current = head;

        while (current != null && current.next != null) {
            if (current.val == current.next.val) {
                current.next = current.next.next;
            } else {
                current = current.next;
            }
        }

        return head;
    }
}
```

Why this works:

```txt
In a sorted list, duplicates are adjacent.
```

---

## Template 13: Skip Every Alternate Node

Example:

```txt
1 → 2 → 3 → 4 → 5 → null
```

After skipping alternate nodes:

```txt
1 → 3 → 5 → null
```

Code:

```java
class Solution {
    public ListNode skipAlternateNodes(ListNode head) {
        ListNode current = head;

        while (current != null && current.next != null) {
            current.next = current.next.next;
            current = current.next;
        }

        return head;
    }
}
```

This is a simple rewiring exercise.

---

## Template 14: Swap First Two Nodes

Use when only the first two nodes need to be swapped.

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

Important:

```txt
Return second because second becomes the new head.
```

---

## Template 15: Swap Two Adjacent Nodes After Previous

Use this when you have:

```txt
previous → first → second → nextNode
```

and you want:

```txt
previous → second → first → nextNode
```

Code:

```java
class Solution {
    public void swapAdjacentAfterPrevious(ListNode previous) {
        if (previous == null || previous.next == null || previous.next.next == null) {
            return;
        }

        ListNode first = previous.next;
        ListNode second = first.next;
        ListNode nextNode = second.next;

        previous.next = second;
        second.next = first;
        first.next = nextNode;
    }
}
```

This template is useful in pair swapping.

---

## Template 16: Swap Values Only

This is not pointer rewiring, but useful for understanding the difference.

```java
class Solution {
    public void swapValues(ListNode first, ListNode second) {
        if (first == null || second == null) {
            return;
        }

        int temp = first.val;
        first.val = second.val;
        second.val = temp;
    }
}
```

Warning:

```txt
This swaps values, not nodes.
Some problems do not allow value swapping.
```

---

## Template 17: Find Previous Node of Target

Use when deletion or insertion needs previous node.

```java
class Solution {
    public ListNode findPreviousOfTarget(ListNode head, int target) {
        if (head == null || head.val == target) {
            return null;
        }

        ListNode previous = head;
        ListNode current = head.next;

        while (current != null) {
            if (current.val == target) {
                return previous;
            }

            previous = current;
            current = current.next;
        }

        return null;
    }
}
```

---

## Template 18: Safe Rewiring Base Template

Use this when links may be changed inside a loop.

```java
class Solution {
    public ListNode safeRewire(ListNode head) {
        ListNode previous = null;
        ListNode current = head;

        while (current != null) {
            ListNode nextNode = current.next;

            // change links here if needed

            previous = current;
            current = nextNode;
        }

        return head;
    }
}
```

Key idea:

```txt
Save nextNode before changing current.next.
```

---

## Template 19: Build New List Using Existing Nodes

Use when moving selected nodes into a result list.

```java
class Solution {
    public ListNode buildUsingExistingNodes(ListNode head) {
        ListNode resultHead = null;
        ListNode resultTail = null;

        ListNode current = head;

        while (current != null) {
            ListNode nextNode = current.next;
            current.next = null;

            if (resultHead == null) {
                resultHead = current;
                resultTail = current;
            } else {
                resultTail.next = current;
                resultTail = current;
            }

            current = nextNode;
        }

        return resultHead;
    }
}
```

This is useful for advanced restructuring problems.

---

## Template 20: Head Change Checklist

Use this when your code modifies the beginning of the list.

```txt
Can head become null?
Can a new node become head?
Can second node become head?
Can head be deleted?
Can head be swapped?
Can head be skipped?
```

Examples:

| Operation | New Head |
|---|---|
| Insert at head | newNode |
| Delete head | head.next |
| Swap first two | second |
| Delete all target values | first non-target node |
| Empty after deletion | null |

---

## Template Selection Guide

| Problem Requirement | Template |
|---|---|
| Add at beginning | Insert at head |
| Add at end | Insert at tail |
| Add after target | Insert after value |
| Add at index | Insert at position |
| Remove first node | Delete head |
| Remove last node | Delete tail |
| Remove first target | Delete first value |
| Remove all targets | Delete all values |
| Remove by index | Delete at position |
| Remove duplicates sorted | Remove duplicates |
| Swap first pair | Swap first two |
| Swap local adjacent pair | Swap adjacent after previous |

---

## Important Coding Rules

```txt
Use current for traversal.
Use previous when deleting current.
Save nextNode before changing current.next if needed.
Return new head when head changes.
Do not move current after deletion if consecutive deletions are possible.
Use current.next != null when you need to stop at last node.
Use current.next.next != null when you need to stop at second last node.
```

---

## Common Rewiring Mistakes

| Mistake | Fix |
|---|---|
| Losing original next node | Save `nextNode` |
| Returning old head | Return updated head |
| Moving current after deletion | Move only when no deletion happened |
| Using `current.next.next` without check | Check `current.next != null` first |
| Swapping values instead of nodes | Change links if node swap is required |
| Incorrect insertion order | Set `newNode.next` before `current.next` |

---

## Final Revision

```txt
Insert after current:
newNode.next = current.next
current.next = newNode

Delete current:
previous.next = current.next

Delete next:
current.next = current.next.next

Swap first two:
second.next = first
first.next = third
return second
```

---

## Day 4 Template Checklist

| Template | Status |
|---|---|
| Insert at head | ✅ |
| Insert at tail | ✅ |
| Insert after node | ✅ |
| Insert after value | ✅ |
| Insert at position | ✅ |
| Delete head | ✅ |
| Delete tail | ✅ |
| Delete first value | ✅ |
| Delete all values | ✅ |
| Delete at position | ✅ |
| Remove duplicates | ✅ |
| Skip alternate nodes | ✅ |
| Swap first two nodes | ✅ |
| Swap adjacent after previous | ✅ |
| Safe rewiring base | ✅ |
