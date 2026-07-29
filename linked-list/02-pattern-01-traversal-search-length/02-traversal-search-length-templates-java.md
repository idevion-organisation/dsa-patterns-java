# Traversal, Search and Length Templates in Java

This file contains reusable Java templates for Pattern 01.

Pattern 01 is used when the problem requires simple node-by-node movement.

Use these templates when the problem asks for:

```txt
traversal
printing
length
search
counting
sum
maximum
minimum
position
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

## Template 1: Basic Traversal

Use when you need to visit every node.

```java
class Solution {
    public void traverse(ListNode head) {
        ListNode current = head;

        while (current != null) {
            // process current node here

            current = current.next;
        }
    }
}
```

Key rule:

```txt
Always move current forward.
```

---

## Template 2: Print All Nodes

```java
class Solution {
    public void printList(ListNode head) {
        ListNode current = head;

        while (current != null) {
            System.out.println(current.val);
            current = current.next;
        }
    }
}
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

## Template 3: Print All Nodes in One Line

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

---

## Template 4: Find Length

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

Used for:

```txt
count nodes
find size
check if list has k nodes
compare lengths of two lists
```

---

## Template 5: Check If List is Empty

```java
class Solution {
    public boolean isEmpty(ListNode head) {
        return head == null;
    }
}
```

---

## Template 6: Check If List Has One Node

```java
class Solution {
    public boolean hasOneNode(ListNode head) {
        return head != null && head.next == null;
    }
}
```

---

## Template 7: Search Target

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

Important:

```txt
Return false only after checking all nodes.
```

---

## Template 8: Find First Position of Target

This template returns the first 0-based position of the target.

```java
class Solution {
    public int findPosition(ListNode head, int target) {
        int position = 0;
        ListNode current = head;

        while (current != null) {
            if (current.val == target) {
                return position;
            }

            position++;
            current = current.next;
        }

        return -1;
    }
}
```

Return:

```txt
position if found
-1 if not found
```

---

## Template 9: Count Occurrences

```java
class Solution {
    public int countOccurrences(ListNode head, int target) {
        int count = 0;
        ListNode current = head;

        while (current != null) {
            if (current.val == target) {
                count++;
            }

            current = current.next;
        }

        return count;
    }
}
```

Used when:

```txt
value may appear multiple times
all matches need to be counted
```

---

## Template 10: Sum of All Nodes

```java
class Solution {
    public int sumOfNodes(ListNode head) {
        int sum = 0;
        ListNode current = head;

        while (current != null) {
            sum += current.val;
            current = current.next;
        }

        return sum;
    }
}
```

---

## Template 11: Find Maximum Value

Use this when the list is guaranteed to be non-empty.

```java
class Solution {
    public int findMax(ListNode head) {
        int maxValue = head.val;
        ListNode current = head.next;

        while (current != null) {
            if (current.val > maxValue) {
                maxValue = current.val;
            }

            current = current.next;
        }

        return maxValue;
    }
}
```

For empty list safety:

```java
if (head == null) {
    throw new IllegalArgumentException("List is empty");
}
```

---

## Template 12: Find Minimum Value

Use this when the list is guaranteed to be non-empty.

```java
class Solution {
    public int findMin(ListNode head) {
        int minValue = head.val;
        ListNode current = head.next;

        while (current != null) {
            if (current.val < minValue) {
                minValue = current.val;
            }

            current = current.next;
        }

        return minValue;
    }
}
```

---

## Template 13: Get Value at Index

Use 0-based indexing.

```java
class Solution {
    public int getValueAtIndex(ListNode head, int index) {
        int position = 0;
        ListNode current = head;

        while (current != null) {
            if (position == index) {
                return current.val;
            }

            position++;
            current = current.next;
        }

        return -1;
    }
}
```

Return `-1` if index is invalid.

Note:

```txt
This is O(n), not O(1).
```

---

## Template 14: Get Node at Index

Use this when you need the actual node reference, not just value.

```java
class Solution {
    public ListNode getNodeAtIndex(ListNode head, int index) {
        int position = 0;
        ListNode current = head;

        while (current != null) {
            if (position == index) {
                return current;
            }

            position++;
            current = current.next;
        }

        return null;
    }
}
```

---

## Template 15: Find Tail Node

The tail node is the last node.

```java
class Solution {
    public ListNode findTail(ListNode head) {
        if (head == null) {
            return null;
        }

        ListNode current = head;

        while (current.next != null) {
            current = current.next;
        }

        return current;
    }
}
```

Important difference:

```java
while (current.next != null)
```

This stops at the last node.

```java
while (current != null)
```

This moves beyond the last node to null.

---

## Template 16: Count Even Values

```java
class Solution {
    public int countEven(ListNode head) {
        int count = 0;
        ListNode current = head;

        while (current != null) {
            if (current.val % 2 == 0) {
                count++;
            }

            current = current.next;
        }

        return count;
    }
}
```

---

## Template 17: Count Odd Values

```java
class Solution {
    public int countOdd(ListNode head) {
        int count = 0;
        ListNode current = head;

        while (current != null) {
            if (current.val % 2 != 0) {
                count++;
            }

            current = current.next;
        }

        return count;
    }
}
```

---

## Template 18: Check If All Values Are Positive

```java
class Solution {
    public boolean allPositive(ListNode head) {
        ListNode current = head;

        while (current != null) {
            if (current.val <= 0) {
                return false;
            }

            current = current.next;
        }

        return true;
    }
}
```

---

## Template 19: Check If Any Value is Negative

```java
class Solution {
    public boolean hasNegative(ListNode head) {
        ListNode current = head;

        while (current != null) {
            if (current.val < 0) {
                return true;
            }

            current = current.next;
        }

        return false;
    }
}
```

---

## Template 20: Compare Lengths of Two Linked Lists

```java
class Solution {
    public boolean haveSameLength(ListNode head1, ListNode head2) {
        int length1 = getLength(head1);
        int length2 = getLength(head2);

        return length1 == length2;
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

Time complexity:

```txt
O(n + m)
```

where:

```txt
n = length of first list
m = length of second list
```

---

## Template 21: Convert Linked List to String

Useful for debugging.

```java
class Solution {
    public String listToString(ListNode head) {
        StringBuilder result = new StringBuilder();
        ListNode current = head;

        while (current != null) {
            result.append(current.val);

            if (current.next != null) {
                result.append(" -> ");
            }

            current = current.next;
        }

        result.append(" -> null");
        return result.toString();
    }
}
```

---

## Template 22: Safe Traversal Checklist

Before submitting traversal code, check:

```txt
Did I initialize current with head?
Did I use current != null?
Did I process current before moving?
Did I move current = current.next?
Did I avoid moving head unnecessarily?
Did I return correct value after the loop?
Did I handle empty list?
```

---

## Template Selection Guide

| Problem Requirement | Use Template |
|---|---|
| Print nodes | Print all nodes |
| Count nodes | Find length |
| Search target | Search target |
| Find index | Find position |
| Count repeated value | Count occurrences |
| Sum values | Sum of nodes |
| Maximum value | Find max |
| Minimum value | Find min |
| Last node | Find tail |
| Value at index | Get value at index |
| Compare two list sizes | Compare lengths |

---

## Common Template Mistakes

| Mistake | Fix |
|---|---|
| Forgetting `current = current.next` | Move current in every loop |
| Returning false inside first failed check | Return false after full traversal |
| Using `head` for traversal | Use `current` |
| Using `head.val` when head is null | Check empty list first |
| Initializing max/min with 0 | Use `head.val` |
| Confusing node and value | Return `ListNode` for node, `int` for value |

---

## Final Revision

```txt
Traversal loop:
current = head
while current != null
process current
current = current.next
```

Search:

```txt
return true when found
return false after loop
```

Length:

```txt
increase count for every node
```

Max/min:

```txt
initialize with head.val
handle empty list
```

---

## Day 3 Template Checklist

| Template | Status |
|---|---|
| Basic traversal | ✅ |
| Print list | ✅ |
| Find length | ✅ |
| Search target | ✅ |
| Find position | ✅ |
| Count occurrences | ✅ |
| Sum nodes | ✅ |
| Find max/min | ✅ |
| Get value at index | ✅ |
| Find tail | ✅ |
| Compare lengths | ✅ |
| Debug print | ✅ |
