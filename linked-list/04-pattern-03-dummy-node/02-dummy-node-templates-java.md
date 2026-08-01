# Dummy Node Templates in Java

This file contains reusable Java templates for Pattern 03.

Dummy Node is used when the head of a linked list may change or when building a new result list becomes difficult without a fake starting node.

Use these templates when the problem involves:

```txt
deleting nodes
removing elements
inserting before head
merging lists
building result lists
handling head edge cases
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

## Template 1: Basic Dummy Node Setup

Use this when the original list may be modified.

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

Key points:

```txt
dummy is fake
dummy.next is real head
current starts from dummy
return dummy.next
```

---

## Template 2: Remove All Target Values

Use when the problem asks:

```txt
remove all nodes with value target
delete all matching nodes
remove elements
```

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

Important:

```txt
Move current only when no deletion happens.
```

---

## Template 3: Delete First Target Value

Use when only the first matching node should be deleted.

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

Difference from removing all:

```txt
Use break after first deletion.
```

---

## Template 4: Remove Nodes by Condition

Use when a node should be removed based on a condition.

Example condition:

```txt
remove nodes greater than x
remove odd nodes
remove negative nodes
remove zero values
```

Template:

```java
class Solution {
    public ListNode removeByCondition(ListNode head) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;

        ListNode current = dummy;

        while (current.next != null) {
            if (shouldRemove(current.next)) {
                current.next = current.next.next;
            } else {
                current = current.next;
            }
        }

        return dummy.next;
    }

    private boolean shouldRemove(ListNode node) {
        return node.val < 0;
    }
}
```

---

## Template 5: Remove Nodes Greater Than X

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

---

## Template 6: Remove Odd Values

```java
class Solution {
    public ListNode removeOddValues(ListNode head) {
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

## Template 7: Keep Only Even Values

This is the same as removing odd values.

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

## Template 8: Remove Negative Values

```java
class Solution {
    public ListNode removeNegativeValues(ListNode head) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;

        ListNode current = dummy;

        while (current.next != null) {
            if (current.next.val < 0) {
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

## Template 9: Insert Before Target

Use when the problem asks:

```txt
insert before first target
insert before a given value
target may be head
```

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

Why dummy helps:

```txt
If target is the original head, dummy acts as previous node.
```

---

## Template 10: Insert Before Every Target

Use when the problem asks to insert before every matching value.

```java
class Solution {
    public ListNode insertBeforeEveryTarget(ListNode head, int target, int value) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;

        ListNode current = dummy;

        while (current.next != null) {
            if (current.next.val == target) {
                ListNode newNode = new ListNode(value);

                newNode.next = current.next;
                current.next = newNode;

                current = newNode.next;
            } else {
                current = current.next;
            }
        }

        return dummy.next;
    }
}
```

Important:

```txt
After inserting before target, move current to the original target.
Otherwise the loop may keep inserting before the same target.
```

---

## Template 11: Build New List Using Dummy and Tail

Use when the result list is newly created.

```java
class Solution {
    public ListNode buildNewList(ListNode head) {
        ListNode dummy = new ListNode(0);
        ListNode tail = dummy;

        ListNode current = head;

        while (current != null) {
            // decide whether to add current value

            tail.next = new ListNode(current.val);
            tail = tail.next;

            current = current.next;
        }

        return dummy.next;
    }
}
```

Key idea:

```txt
dummy gives fixed start
tail helps append nodes easily
```

---

## Template 12: Build Filtered List

Use when only selected values should be copied.

```java
class Solution {
    public ListNode buildFilteredList(ListNode head, int x) {
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

Space complexity:

```txt
O(n)
```

because new nodes are created.

---

## Template 13: Copy Full Linked List

```java
class Solution {
    public ListNode copyList(ListNode head) {
        ListNode dummy = new ListNode(0);
        ListNode tail = dummy;

        ListNode current = head;

        while (current != null) {
            tail.next = new ListNode(current.val);
            tail = tail.next;

            current = current.next;
        }

        return dummy.next;
    }
}
```

---

## Template 14: Merge Two Sorted Lists

Use when the problem asks:

```txt
merge two sorted linked lists
combine two sorted lists
return sorted merged list
```

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

Complexity:

```txt
Time Complexity: O(n + m)
Space Complexity: O(1)
```

---

## Template 15: Merge Two Lists by Creating New Nodes

Use when original lists should not be modified.

```java
class Solution {
    public ListNode mergeTwoListsCopy(ListNode list1, ListNode list2) {
        ListNode dummy = new ListNode(0);
        ListNode tail = dummy;

        while (list1 != null && list2 != null) {
            if (list1.val <= list2.val) {
                tail.next = new ListNode(list1.val);
                list1 = list1.next;
            } else {
                tail.next = new ListNode(list2.val);
                list2 = list2.next;
            }

            tail = tail.next;
        }

        while (list1 != null) {
            tail.next = new ListNode(list1.val);
            tail = tail.next;
            list1 = list1.next;
        }

        while (list2 != null) {
            tail.next = new ListNode(list2.val);
            tail = tail.next;
            list2 = list2.next;
        }

        return dummy.next;
    }
}
```

Complexity:

```txt
Time Complexity: O(n + m)
Space Complexity: O(n + m)
```

---

## Template 16: Remove Duplicates From Sorted List II

Problem type:

```txt
sorted linked list
remove all values that appear more than once
keep only distinct values
```

Example:

```txt
Input:
1 → 2 → 3 → 3 → 4 → 4 → 5 → null

Output:
1 → 2 → 5 → null
```

Code:

```java
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;

        ListNode previous = dummy;
        ListNode current = head;

        while (current != null) {
            boolean hasDuplicate = false;

            while (current.next != null && current.val == current.next.val) {
                hasDuplicate = true;
                current = current.next;
            }

            if (hasDuplicate) {
                previous.next = current.next;
            } else {
                previous = previous.next;
            }

            current = current.next;
        }

        return dummy.next;
    }
}
```

Why dummy is useful:

```txt
The first value itself may be duplicated and removed.
So head can change.
```

---

## Template 17: Partition List Around X

Problem type:

```txt
nodes less than x come before nodes greater than or equal to x
relative order should be preserved
```

Example:

```txt
Input:
1 → 4 → 3 → 2 → 5 → 2 → null
x = 3

Output:
1 → 2 → 2 → 4 → 3 → 5 → null
```

Code:

```java
class Solution {
    public ListNode partition(ListNode head, int x) {
        ListNode beforeDummy = new ListNode(0);
        ListNode afterDummy = new ListNode(0);

        ListNode beforeTail = beforeDummy;
        ListNode afterTail = afterDummy;

        ListNode current = head;

        while (current != null) {
            if (current.val < x) {
                beforeTail.next = current;
                beforeTail = beforeTail.next;
            } else {
                afterTail.next = current;
                afterTail = afterTail.next;
            }

            current = current.next;
        }

        afterTail.next = null;
        beforeTail.next = afterDummy.next;

        return beforeDummy.next;
    }
}
```

Important:

```txt
Set afterTail.next = null to avoid accidental cycles.
```

---

## Template 18: Add Two Numbers Basic Dummy Setup

Problem type:

```txt
two linked lists represent numbers
add digits
carry is generated
build result list
```

Dummy is useful because result list is built node by node.

```java
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode dummy = new ListNode(0);
        ListNode tail = dummy;

        int carry = 0;

        while (l1 != null || l2 != null || carry != 0) {
            int sum = carry;

            if (l1 != null) {
                sum += l1.val;
                l1 = l1.next;
            }

            if (l2 != null) {
                sum += l2.val;
                l2 = l2.next;
            }

            carry = sum / 10;
            int digit = sum % 10;

            tail.next = new ListNode(digit);
            tail = tail.next;
        }

        return dummy.next;
    }
}
```

This full pattern will be covered later in Carry Pattern.

---

## Template 19: Dummy Node With Fast and Slow

Dummy node is often combined with two pointers.

Example use:

```txt
remove nth node from end
```

Basic setup:

```java
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
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

        slow.next = slow.next.next;

        return dummy.next;
    }
}
```

Note:

```txt
This combines Dummy Node + Two Pointers Gap.
The complete gap pattern will be covered later.
```

---

## Template 20: Dummy Return Checklist

Whenever dummy is used, check:

```txt
Did I create dummy?
Did I connect dummy.next = head?
Did I start current from dummy when deleting?
Did I use tail = dummy when building?
Did I return dummy.next?
Did I avoid returning dummy?
```

---

## Template Selection Guide

| Problem Requirement | Template |
|---|---|
| Remove all target nodes | Remove all target values |
| Delete first target only | Delete first target value |
| Remove by condition | Remove nodes by condition |
| Insert before target | Insert before target |
| Build a copied list | Build new list / copy list |
| Filter values into new list | Build filtered list |
| Merge sorted lists | Merge two lists |
| Delete all duplicate values | Remove duplicates from sorted list II |
| Partition list | Partition with two dummy nodes |
| Add two numbers | Dummy + tail + carry |
| Remove nth from end | Dummy + gap pointers |

---

## Dummy Node Rules

```txt
Dummy is fake.
Dummy should point to head.
For deletion, start current from dummy.
For building, start tail from dummy.
For merging, start tail from dummy.
Return dummy.next.
Do not return dummy.
Do not forget dummy.next = head.
```

---

## Common Mistakes

| Mistake | Correct Fix |
|---|---|
| Returning dummy | Return dummy.next |
| Forgetting dummy.next = head | Connect dummy to head |
| Moving current after deletion | Move only when no deletion |
| Using current instead of current.next for deletion | Delete current.next using current |
| Not using tail for building list | Use tail to append |
| Creating new nodes when original nodes should be reused | Read problem carefully |
| Reusing nodes but not cutting tail | Set final tail.next = null when needed |

---

## Final Revision

```txt
Deletion with dummy:
dummy.next = head
current = dummy
if current.next should be removed:
    current.next = current.next.next
else:
    current = current.next
return dummy.next
```

```txt
Building with dummy:
dummy = new node
tail = dummy
tail.next = new node
tail = tail.next
return dummy.next
```

```txt
Merging with dummy:
dummy = new node
tail = dummy
attach smaller node
move tail
return dummy.next
```

---

## Day 5 Template Checklist

| Template | Status |
|---|---|
| Basic dummy setup | ✅ |
| Remove all target values | ✅ |
| Delete first target | ✅ |
| Remove by condition | ✅ |
| Remove odd/negative/greater values | ✅ |
| Insert before target | ✅ |
| Build new list | ✅ |
| Build filtered list | ✅ |
| Copy full list | ✅ |
| Merge two sorted lists | ✅ |
| Remove duplicates II | ✅ |
| Partition list | ✅ |
| Add two numbers setup | ✅ |
| Remove nth setup preview | ✅ |
