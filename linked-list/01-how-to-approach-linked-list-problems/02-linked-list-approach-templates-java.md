# Linked List Approach Templates in Java

This file contains beginner-friendly templates for approaching linked list problems.

These are not final pattern solutions.

These are base structures that help you start linked list problems correctly.

Use these templates to avoid common mistakes with:

```txt
head
current
previous
nextNode
dummy
slow
fast
tail
```

---

## Basic ListNode Template

Most linked list problems use this node structure.

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

## Template 1: Basic Traversal

Use this when the problem asks to:

```txt
print nodes
count nodes
search value
sum values
find maximum/minimum
```

Template:

```java
class Solution {
    public void traverse(ListNode head) {
        ListNode current = head;

        while (current != null) {
            // process current node
            current = current.next;
        }
    }
}
```

Key idea:

```txt
Use current pointer.
Do not move head directly.
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

## Template 2: Count Length

Use this when the problem asks:

```txt
find length
count nodes
return number of nodes
```

Template:

```java
class Solution {
    public int getLength(ListNode head) {
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

---

## Template 3: Search a Value

Use this when the problem asks:

```txt
check if value exists
find target
search node
```

Template:

```java
class Solution {
    public boolean search(ListNode head, int target) {
        ListNode current = head;

        while (current != null) {
            if (current.val == target) {
                return true;
            }

            current = current.next;
        }

        return false;
    }
}
```

---

## Template 4: Previous and Current Traversal

Use this when the problem involves:

```txt
deletion
insertion
removing elements
skipping nodes
rewiring links
```

Template:

```java
class Solution {
    public ListNode process(ListNode head) {
        ListNode previous = null;
        ListNode current = head;

        while (current != null) {
            // process current node

            previous = current;
            current = current.next;
        }

        return head;
    }
}
```

Pointer meaning:

```txt
previous → node before current
current  → node being processed
```

---

## Template 5: Safe Rewiring Template

Use this when you are about to change `current.next`.

Template:

```java
class Solution {
    public ListNode rewire(ListNode head) {
        ListNode previous = null;
        ListNode current = head;

        while (current != null) {
            ListNode nextNode = current.next;

            // change links safely here

            previous = current;
            current = nextNode;
        }

        return head;
    }
}
```

Important:

```txt
Save nextNode before changing current.next.
```

---

## Template 6: Dummy Node Template

Use this when:

```txt
head may be deleted
head may change
new list is being built
merge operation is needed
deletion edge cases are difficult
```

Template:

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

Why return `dummy.next`?

```txt
Because dummy is fake.
The real list starts from dummy.next.
```

---

## Template 7: Delete Using Dummy Node

Use this when the problem asks to delete nodes by condition.

```java
class Solution {
    public ListNode removeNodes(ListNode head, int target) {
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

This handles:

```txt
target at head
target in middle
target at tail
multiple target nodes
empty list
```

---

## Template 8: Fast and Slow Pointer Setup

Use this when the problem asks:

```txt
middle node
cycle detection
split linked list
palindrome linked list
```

Template:

```java
class Solution {
    public void fastSlow(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;

        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }

        // slow is at middle position in many problems
    }
}
```

Important condition:

```java
while (fast != null && fast.next != null)
```

This prevents NullPointerException.

---

## Template 9: Two Pointers Gap Setup

Use this when the problem asks:

```txt
nth node from end
remove nth node from end
fixed distance between two nodes
```

Template:

```java
class Solution {
    public ListNode gapPointer(ListNode head, int n) {
        ListNode fast = head;
        ListNode slow = head;

        for (int i = 0; i < n; i++) {
            if (fast == null) {
                return head;
            }
            fast = fast.next;
        }

        while (fast != null) {
            slow = slow.next;
            fast = fast.next;
        }

        return slow;
    }
}
```

Meaning:

```txt
fast is n steps ahead of slow.
When fast reaches end, slow is at required position.
```

---

## Template 10: Reversal Base Setup

Use this when the problem asks:

```txt
reverse list
reverse part of list
reverse k-group
reorder list
palindrome list
```

Template:

```java
class Solution {
    public ListNode reverse(ListNode head) {
        ListNode previous = null;
        ListNode current = head;

        while (current != null) {
            ListNode nextNode = current.next;

            current.next = previous;

            previous = current;
            current = nextNode;
        }

        return previous;
    }
}
```

Pointer meaning:

```txt
previous → reversed part
current  → current node being reversed
nextNode → remaining list
```

---

## Template 11: Merge Two Lists Setup

Use this when the problem asks:

```txt
merge two sorted linked lists
combine two lists
build result list
```

Template:

```java
class Solution {
    public ListNode merge(ListNode list1, ListNode list2) {
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

Why dummy and tail?

```txt
dummy helps build the result list easily
tail tracks the end of the result list
```

---

## Template 12: Edge Case Guard

Use this at the beginning when needed:

```java
if (head == null) {
    return null;
}
```

For single-node checks:

```java
if (head == null || head.next == null) {
    return head;
}
```

Use this when:

```txt
reversal
middle logic
delete logic
split logic
cycle logic
```

---

## Template 13: Return Type Decision

If problem says:

```txt
return modified linked list
```

then use:

```java
return head;
```

or:

```java
return dummy.next;
```

or:

```java
return newHead;
```

If problem says:

```txt
return true/false
```

then return:

```java
return true;
return false;
```

If problem says:

```txt
return count/length/value
```

then return:

```java
return count;
return length;
return value;
```

---

## Template 14: Manual Debug Print

Use this while learning.

```java
class Solution {
    public void printList(ListNode head) {
        ListNode current = head;

        while (current != null) {
            System.out.print(current.val + " ");
            current = current.next;
        }

        System.out.println();
    }
}
```

This helps verify your pointer changes.

---

## Template Selection Guide

| Problem Type | Template to Start With |
|---|---|
| Count nodes | Basic traversal / length |
| Search value | Search template |
| Delete node | Previous-current or dummy |
| Remove head possible | Dummy node |
| Reverse list | Reversal setup |
| Find middle | Fast-slow |
| Detect cycle | Fast-slow |
| Remove nth from end | Gap pointer + dummy |
| Merge lists | Dummy + tail |
| Build new list | Dummy + tail |

---

## Important Coding Rules

```txt
Do not move head unless necessary.
Use current for traversal.
Use dummy when head can change.
Save nextNode before changing current.next.
Check fast and fast.next before moving fast two steps.
Return dummy.next when dummy is used.
Dry run empty and single-node cases.
```

---

## Day 2 Template Checklist

| Template | Status |
|---|---|
| ListNode class | ✅ |
| Traversal | ✅ |
| Length | ✅ |
| Search | ✅ |
| Previous-current | ✅ |
| Safe rewiring | ✅ |
| Dummy node | ✅ |
| Fast-slow | ✅ |
| Gap pointer | ✅ |
| Reversal base | ✅ |
| Merge base | ✅ |
| Edge case guard | ✅ |
