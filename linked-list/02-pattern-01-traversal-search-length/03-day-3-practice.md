# Day 3 Practice: Traversal, Search and Length

This practice file is for Pattern 01 of Linked List.

The goal is to become comfortable with:

```txt
moving current pointer
checking null
counting nodes
searching values
processing every node
handling edge cases
```

Do not rush this pattern.

Most linked list bugs start from weak traversal understanding.

---

## Practice Method

For every question, write:

```txt
Initial current:
Loop condition:
What is processed:
How current moves:
When loop stops:
Time complexity:
Space complexity:
```

---

## Practice 1: Trace Traversal

Given:

```txt
head → 10 → 20 → 30 → null
```

Code:

```java
ListNode current = head;

while (current != null) {
    System.out.println(current.val);
    current = current.next;
}
```

Fill the dry run:

| Step | current value | Printed | next current |
|---:|---:|---:|---|
| 1 | 10 | 10 | 20 |
| 2 | 20 | 20 | 30 |
| 3 | 30 | 30 | null |
| 4 | null | stop | end |

Output:

```txt
10
20
30
```

---

## Practice 2: Find Length Manually

Given:

```txt
head → 5 → 15 → 25 → 35 → null
```

Find length.

Answer:

```txt
4
```

Dry run:

| Node visited | length |
|---:|---:|
| 5 | 1 |
| 15 | 2 |
| 25 | 3 |
| 35 | 4 |

---

## Practice 3: Search Existing Target

Given:

```txt
head → 4 → 8 → 12 → 16 → null
target = 12
```

Answer:

```txt
true
```

Reason:

```txt
12 exists in the linked list.
```

Dry run:

| Step | current value | Match target? |
|---:|---:|---|
| 1 | 4 | No |
| 2 | 8 | No |
| 3 | 12 | Yes |

---

## Practice 4: Search Missing Target

Given:

```txt
head → 4 → 8 → 12 → 16 → null
target = 20
```

Answer:

```txt
false
```

Reason:

```txt
Traversal reaches null without finding 20.
```

---

## Practice 5: Empty List

Given:

```txt
head → null
```

Answer:

| Operation | Result |
|---|---|
| Print | Nothing |
| Length | 0 |
| Search any value | false |
| Count occurrences | 0 |
| Sum | 0 |

---

## Practice 6: Single Node List

Given:

```txt
head → 100 → null
```

Answer:

| Operation | Result |
|---|---|
| Length | 1 |
| Search 100 | true |
| Search 50 | false |
| Sum | 100 |
| Max | 100 |
| Min | 100 |

---

## Practice 7: Count Occurrences

Given:

```txt
head → 2 → 5 → 2 → 7 → 2 → null
target = 2
```

Answer:

```txt
3
```

Dry run:

| Step | current value | count |
|---:|---:|---:|
| 1 | 2 | 1 |
| 2 | 5 | 1 |
| 3 | 2 | 2 |
| 4 | 7 | 2 |
| 5 | 2 | 3 |

---

## Practice 8: Sum of Nodes

Given:

```txt
head → 10 → 20 → 30 → 40 → null
```

Find sum.

Answer:

```txt
100
```

Dry run:

| Node | sum |
|---:|---:|
| 10 | 10 |
| 20 | 30 |
| 30 | 60 |
| 40 | 100 |

---

## Practice 9: Find Maximum

Given:

```txt
head → 3 → 9 → 2 → 15 → 7 → null
```

Answer:

```txt
15
```

Reason:

```txt
15 is the largest value.
```

---

## Practice 10: Find Minimum

Given:

```txt
head → 3 → 9 → 2 → 15 → 7 → null
```

Answer:

```txt
2
```

Reason:

```txt
2 is the smallest value.
```

---

## Practice 11: Find Position

Given:

```txt
head → 10 → 20 → 30 → 40 → null
target = 30
```

Use 0-based indexing.

Answer:

```txt
2
```

Dry run:

| Node value | position |
|---:|---:|
| 10 | 0 |
| 20 | 1 |
| 30 | 2 |

---

## Practice 12: Target Not Found Position

Given:

```txt
head → 10 → 20 → 30 → null
target = 50
```

Answer:

```txt
-1
```

Reason:

```txt
50 is not present in the linked list.
```

---

## Practice 13: Identify Mistake

Code:

```java
ListNode current = head;

while (current != null) {
    System.out.println(current.val);
}
```

Question:

```txt
What is wrong?
```

Answer:

```txt
current is never moved to current.next.
This causes an infinite loop.
```

Correct code:

```java
ListNode current = head;

while (current != null) {
    System.out.println(current.val);
    current = current.next;
}
```

---

## Practice 14: Identify Search Mistake

Wrong code:

```java
class Solution {
    public boolean search(ListNode head, int target) {
        ListNode current = head;

        while (current != null) {
            if (current.val == target) {
                return true;
            } else {
                return false;
            }
        }

        return false;
    }
}
```

Question:

```txt
Why is this wrong?
```

Answer:

```txt
It returns false after checking only the first node.

Search should return false only after checking all nodes.
```

Correct code:

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

## Practice 15: Fill the Blank

Complete the traversal code.

```java
class Solution {
    public void printList(ListNode head) {
        ListNode current = _____;

        while (current != null) {
            System.out.println(current.val);
            current = _____;
        }
    }
}
```

Answer:

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

---

## Practice 16: Write Length Function

Task:

```txt
Write a function to return linked list length.
```

Solution:

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

Complexity:

```txt
Time Complexity: O(n)
Space Complexity: O(1)
```

---

## Practice 17: Write Search Function

Task:

```txt
Return true if target exists.
```

Solution:

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

## Practice 18: Write Count Occurrences Function

Task:

```txt
Count how many times target appears.
```

Solution:

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

---

## Practice 19: Write Sum Function

Task:

```txt
Return sum of all node values.
```

Solution:

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

## Practice 20: Write Position Function

Task:

```txt
Return first 0-based position of target.
Return -1 if target is not found.
```

Solution:

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

---

## Practice 21: MCQ Check

### Q1. Which pointer is commonly used for traversal?

```txt
A. current
B. random
C. index
D. pivot
```

Answer:

```txt
A. current
```

---

### Q2. What is the correct loop condition for full traversal?

```txt
A. while (current.next != null)
B. while (current != null)
C. while (head.next == null)
D. while (current.val != null)
```

Answer:

```txt
B. while (current != null)
```

---

### Q3. What happens if we forget `current = current.next`?

```txt
A. List reverses
B. Infinite loop may happen
C. Search becomes O(1)
D. Head changes automatically
```

Answer:

```txt
B. Infinite loop may happen
```

---

### Q4. What is the time complexity of finding length?

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

### Q5. When should search return false?

```txt
A. After first node does not match
B. After reaching null without finding target
C. Before loop starts always
D. When current is head
```

Answer:

```txt
B. After reaching null without finding target
```

---

## Practice 22: Complexity Table

Fill the complexities:

| Operation | Time | Space |
|---|---:|---:|
| Print all nodes | O(n) | O(1) |
| Find length | O(n) | O(1) |
| Search target | O(n) | O(1) |
| Count occurrences | O(n) | O(1) |
| Sum nodes | O(n) | O(1) |
| Find max/min | O(n) | O(1) |
| Find position | O(n) | O(1) |

---

## Practice 23: Edge Case Checklist

Test every traversal-based function on:

```txt
head = null
head = 10 → null
head = 10 → 20 → null
head = 10 → 20 → 30 → null
target at head
target at tail
target not present
duplicate target values
negative values
```

---

## Practice 24: Mini Problem Set

Try writing code for these without looking at templates.

```txt
1. Print all nodes
2. Return length of linked list
3. Search for target
4. Count occurrences of target
5. Return sum of all values
6. Return maximum value
7. Return minimum value
8. Return first position of target
9. Return value at given index
10. Count even values
```

---

## Practice 25: Answer Key Summary

| Problem | Main Idea |
|---|---|
| Print all nodes | Traverse and print |
| Find length | Traverse and count |
| Search target | Traverse and compare |
| Count occurrences | Traverse and count matches |
| Sum nodes | Traverse and add |
| Max/min | Traverse and compare |
| Position | Traverse with index counter |
| Value at index | Traverse with position |
| Count even | Traverse and check `% 2 == 0` |

---

## Common Mistakes to Avoid

| Mistake | Correct Thinking |
|---|---|
| Moving head directly | Use current |
| Missing current movement | Add current = current.next |
| Returning false too early | Return false after loop |
| Accessing current.val when current is null | Check current != null |
| Using index like array | Linked list moves node by node |
| Forgetting empty list | Test head == null |
| Starting max/min from 0 | Start from head.val |

---

## Day 3 Final Revision

```txt
Traversal pattern is the base of linked list.

Start:
current = head

Loop:
while current != null

Process:
use current.val

Move:
current = current.next

Stop:
current becomes null
```

---

## Day 3 Completion Checklist

| Task | Status |
|---|---|
| Dry run traversal | ✅ |
| Print all nodes | ✅ |
| Find length | ✅ |
| Search target | ✅ |
| Count occurrences | ✅ |
| Find sum | ✅ |
| Find max/min | ✅ |
| Find position | ✅ |
| Understand O(n) time | ✅ |
| Understand O(1) space | ✅ |
| Avoid infinite loop | ✅ |
| Avoid early false return | ✅ |
| Handle edge cases | ✅ |
