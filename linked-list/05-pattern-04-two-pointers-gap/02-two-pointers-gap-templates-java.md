# Two Pointers Gap Templates in Java

This file contains reusable Java templates for Pattern 04.

The Two Pointers Gap Pattern is used when one pointer must stay a fixed distance ahead of another pointer.

Use these templates when the problem involves:

```txt
nth node from end
kth node from end
remove nth node from end
delete kth node from end
fixed distance
length difference
aligning linked lists
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

## Template 1: Move Pointer K Steps

This is the base helper for gap pattern.

```java
class Solution {
    public ListNode moveKSteps(ListNode node, int k) {
        ListNode current = node;

        for (int i = 0; i < k; i++) {
            if (current == null) {
                return null;
            }

            current = current.next;
        }

        return current;
    }
}
```

Used for:

```txt
creating gap
checking list length
moving longer list pointer
advanced linked list patterns
```

---

## Template 2: Check If List Has At Least K Nodes

```java
class Solution {
    public boolean hasAtLeastKNodes(ListNode head, int k) {
        if (k <= 0) {
            return true;
        }

        ListNode current = head;

        for (int i = 0; i < k; i++) {
            if (current == null) {
                return false;
            }

            current = current.next;
        }

        return true;
    }
}
```

Example:

```txt
10 → 20 → 30 → null
k = 3
```

Answer:

```txt
true
```

Example:

```txt
10 → 20 → 30 → null
k = 4
```

Answer:

```txt
false
```

---

## Template 3: Find Nth Node From End

```java
class Solution {
    public ListNode findNthFromEnd(ListNode head, int n) {
        if (head == null || n <= 0) {
            return null;
        }

        ListNode fast = head;
        ListNode slow = head;

        for (int i = 0; i < n; i++) {
            if (fast == null) {
                return null;
            }

            fast = fast.next;
        }

        while (fast != null) {
            fast = fast.next;
            slow = slow.next;
        }

        return slow;
    }
}
```

Key idea:

```txt
fast is n steps ahead.
When fast reaches null, slow is nth from end.
```

---

## Template 4: Find Kth Node From End

Same as nth node from end.

```java
class Solution {
    public ListNode findKthFromEnd(ListNode head, int k) {
        if (head == null || k <= 0) {
            return null;
        }

        ListNode fast = head;
        ListNode slow = head;

        for (int i = 0; i < k; i++) {
            if (fast == null) {
                return null;
            }

            fast = fast.next;
        }

        while (fast != null) {
            fast = fast.next;
            slow = slow.next;
        }

        return slow;
    }
}
```

---

## Template 5: Find Value of Nth Node From End

```java
class Solution {
    public int findNthValueFromEnd(ListNode head, int n) {
        ListNode node = findNthFromEnd(head, n);

        if (node == null) {
            return -1;
        }

        return node.val;
    }

    private ListNode findNthFromEnd(ListNode head, int n) {
        if (head == null || n <= 0) {
            return null;
        }

        ListNode fast = head;
        ListNode slow = head;

        for (int i = 0; i < n; i++) {
            if (fast == null) {
                return null;
            }

            fast = fast.next;
        }

        while (fast != null) {
            fast = fast.next;
            slow = slow.next;
        }

        return slow;
    }
}
```

Note:

```txt
Return -1 is only a beginner-friendly choice.
In real problems, follow the required return format.
```

---

## Template 6: Remove Nth Node From End

Use dummy node because the head may be removed.

```java
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        if (n <= 0) {
            return head;
        }

        ListNode dummy = new ListNode(0);
        dummy.next = head;

        ListNode fast = dummy;
        ListNode slow = dummy;

        for (int i = 0; i <= n; i++) {
            if (fast == null) {
                return head;
            }

            fast = fast.next;
        }

        while (fast != null) {
            fast = fast.next;
            slow = slow.next;
        }

        slow.next = slow.next.next;

        return dummy.next;
    }
}
```

Important:

```txt
Move fast n + 1 steps from dummy.
This makes slow stop before the node to delete.
```

---

## Template 7: Delete Kth Node From End

```java
class Solution {
    public ListNode deleteKthFromEnd(ListNode head, int k) {
        if (k <= 0) {
            return head;
        }

        ListNode dummy = new ListNode(0);
        dummy.next = head;

        ListNode fast = dummy;
        ListNode slow = dummy;

        for (int i = 0; i <= k; i++) {
            if (fast == null) {
                return head;
            }

            fast = fast.next;
        }

        while (fast != null) {
            fast = fast.next;
            slow = slow.next;
        }

        slow.next = slow.next.next;

        return dummy.next;
    }
}
```

---

## Template 8: Find Previous of Nth Node From End

```java
class Solution {
    public ListNode findPreviousOfNthFromEnd(ListNode head, int n) {
        if (n <= 0) {
            return null;
        }

        ListNode dummy = new ListNode(0);
        dummy.next = head;

        ListNode fast = dummy;
        ListNode slow = dummy;

        for (int i = 0; i <= n; i++) {
            if (fast == null) {
                return null;
            }

            fast = fast.next;
        }

        while (fast != null) {
            fast = fast.next;
            slow = slow.next;
        }

        return slow;
    }
}
```

Use this when:

```txt
you need the node before nth from end
you want to delete slow.next
you want to inspect previous node
```

---

## Template 9: Remove Nth From End Using Length

This is not the main gap pattern, but useful for comparison.

```java
class Solution {
    public ListNode removeNthFromEndUsingLength(ListNode head, int n) {
        if (n <= 0) {
            return head;
        }

        int length = getLength(head);

        if (n > length) {
            return head;
        }

        int positionFromStart = length - n;

        ListNode dummy = new ListNode(0);
        dummy.next = head;

        ListNode current = dummy;

        for (int i = 0; i < positionFromStart; i++) {
            current = current.next;
        }

        current.next = current.next.next;

        return dummy.next;
    }

    private int getLength(ListNode head) {
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

Comparison:

```txt
Length method → two passes
Gap method → one pass
```

---

## Template 10: Find Length Difference Between Two Lists

```java
class Solution {
    public int getLengthDifference(ListNode headA, ListNode headB) {
        int lengthA = getLength(headA);
        int lengthB = getLength(headB);

        return Math.abs(lengthA - lengthB);
    }

    private int getLength(ListNode head) {
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

Used before aligning two linked lists.

---

## Template 11: Move Longer List Pointer by Gap

```java
class Solution {
    public ListNode moveLongerPointer(ListNode longerHead, int gap) {
        ListNode current = longerHead;

        for (int i = 0; i < gap; i++) {
            if (current == null) {
                return null;
            }

            current = current.next;
        }

        return current;
    }
}
```

Used for:

```txt
intersection of linked lists
aligning two lists
comparing equal remaining lengths
```

---

## Template 12: Align Two List Pointers

This is a preview of intersection-style problems.

```java
class Solution {
    public ListNode[] alignTwoLists(ListNode headA, ListNode headB) {
        int lengthA = getLength(headA);
        int lengthB = getLength(headB);

        ListNode pointerA = headA;
        ListNode pointerB = headB;

        if (lengthA > lengthB) {
            int gap = lengthA - lengthB;

            for (int i = 0; i < gap; i++) {
                pointerA = pointerA.next;
            }
        } else {
            int gap = lengthB - lengthA;

            for (int i = 0; i < gap; i++) {
                pointerB = pointerB.next;
            }
        }

        return new ListNode[] { pointerA, pointerB };
    }

    private int getLength(ListNode head) {
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

Note:

```txt
This only aligns the starting pointers.
Full intersection solving will be covered later.
```

---

## Template 13: Find Nth From End Value With Error Message Style

Use this for beginner debugging.

```java
class Solution {
    public void printNthFromEnd(ListNode head, int n) {
        ListNode node = findNthFromEnd(head, n);

        if (node == null) {
            System.out.println("Invalid n or list is too short");
        } else {
            System.out.println(node.val);
        }
    }

    private ListNode findNthFromEnd(ListNode head, int n) {
        if (head == null || n <= 0) {
            return null;
        }

        ListNode fast = head;
        ListNode slow = head;

        for (int i = 0; i < n; i++) {
            if (fast == null) {
                return null;
            }

            fast = fast.next;
        }

        while (fast != null) {
            fast = fast.next;
            slow = slow.next;
        }

        return slow;
    }
}
```

---

## Template 14: Gap Pattern Base Template

Use this as the starting skeleton.

```java
class Solution {
    public ListNode gapPattern(ListNode head, int gap) {
        if (head == null || gap <= 0) {
            return head;
        }

        ListNode fast = head;
        ListNode slow = head;

        for (int i = 0; i < gap; i++) {
            if (fast == null) {
                return null;
            }

            fast = fast.next;
        }

        while (fast != null) {
            fast = fast.next;
            slow = slow.next;
        }

        return slow;
    }
}
```

---

## Template 15: Gap Pattern With Dummy Base

Use this when deletion is involved.

```java
class Solution {
    public ListNode gapPatternWithDummy(ListNode head, int gap) {
        if (gap <= 0) {
            return head;
        }

        ListNode dummy = new ListNode(0);
        dummy.next = head;

        ListNode fast = dummy;
        ListNode slow = dummy;

        for (int i = 0; i <= gap; i++) {
            if (fast == null) {
                return head;
            }

            fast = fast.next;
        }

        while (fast != null) {
            fast = fast.next;
            slow = slow.next;
        }

        // slow is before the target node
        // delete if needed:
        // slow.next = slow.next.next;

        return dummy.next;
    }
}
```

---

## Template Selection Guide

| Problem Requirement | Template |
|---|---|
| Move pointer k steps | Move Pointer K Steps |
| Check at least k nodes | Has At Least K Nodes |
| Find nth from end | Find Nth Node From End |
| Find kth from end | Find Kth Node From End |
| Return nth value from end | Find Value of Nth Node |
| Remove nth from end | Remove Nth Node From End |
| Delete kth from end | Delete Kth Node From End |
| Need previous node before target from end | Find Previous of Nth |
| Compare gap vs length | Remove Using Length |
| Align two lists | Align Two List Pointers |

---

## Important Coding Rules

```txt
Create the gap before moving both pointers.
Do not move slow during gap creation.
Check fast before moving it.
Use dummy when deletion may change head.
For deletion, slow should stop before target.
Return dummy.next when dummy is used.
Do not confuse gap pattern with fast-slow pattern.
```

---

## Common Template Mistakes

| Mistake | Correct Fix |
|---|---|
| Moving slow while creating gap | Move only fast first |
| Using `fast.next` without null check | Check fast safely |
| Moving fast n instead of n + 1 for deletion with dummy | Use n + 1 gap from dummy |
| Returning dummy | Return dummy.next |
| Not handling n greater than length | Return null or unchanged list |
| Confusing kth from end with kth from start | Use gap pattern |
| Using fast two steps | That is fast-slow, not gap |

---

## Final Revision

```txt
Find nth from end:
fast = head
slow = head
move fast n steps
move both until fast is null
return slow
```

```txt
Remove nth from end:
dummy.next = head
fast = dummy
slow = dummy
move fast n + 1 steps
move both until fast is null
slow.next = slow.next.next
return dummy.next
```

---

## Day 6 Template Checklist

| Template | Status |
|---|---|
| Move k steps | ✅ |
| Check at least k nodes | ✅ |
| Find nth from end | ✅ |
| Find kth from end | ✅ |
| Find nth value from end | ✅ |
| Remove nth from end | ✅ |
| Delete kth from end | ✅ |
| Find previous of nth | ✅ |
| Length-based comparison | ✅ |
| Move longer pointer by gap | ✅ |
| Align two list pointers | ✅ |
| Dummy + gap setup | ✅ |
