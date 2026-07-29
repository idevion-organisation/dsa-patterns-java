# Pattern 01: Traversal, Search and Length

Traversal is the first and most important linked list pattern.

Before solving deletion, reversal, cycle detection, middle node, merge, palindrome, or advanced linked list problems, you must be comfortable with moving through a linked list node by node.

This pattern teaches how to:

```txt
visit every node
search for a value
count nodes
find length
process node values
stop safely at null
avoid losing head
```

---

## Why This Pattern Matters

In arrays, we move using indexes:

```java
arr[i]
```

In linked list, there is no direct index access.

We move using references:

```java
current = current.next;
```

That means linked list traversal is the base skill behind almost every linked list problem.

If traversal is weak, every next linked list pattern will feel difficult.

---

## Pattern Name

```txt
Traversal, Search and Length
```

---

## Pattern Goal

The goal of this pattern is to move through a linked list safely from the head node to the end of the list.

Basic structure:

```txt
start from head
visit current node
move to next node
stop at null
```

---

## Basic Linked List Example

```txt
head → 10 → 20 → 30 → 40 → null
```

Traversal order:

```txt
10
20
30
40
```

The traversal stops when `current` becomes `null`.

---

## Pattern Signal

Use this pattern when the problem says:

```txt
print all nodes
find length
count nodes
search for a value
find maximum value
find minimum value
calculate sum
count occurrences
check if a value exists
find position of a value
visit every node
```

Common problem statements:

```txt
Given the head of a linked list, return its length.
Given the head of a linked list, search for a target value.
Given the head of a linked list, print all node values.
Given the head of a linked list, count how many times a value appears.
```

---

## Main Pointer Used

This pattern mainly uses one pointer:

```txt
current
```

`current` is a temporary pointer used to move through the list.

```java
ListNode current = head;
```

Important:

```txt
Do not move head directly unless the problem specifically allows it.
```

---

## Why We Do Not Move Head Directly

Wrong approach:

```java
while (head != null) {
    System.out.println(head.val);
    head = head.next;
}
```

This works for printing, but it moves the original `head`.

After the loop:

```txt
head = null
```

The starting point of the list is lost.

Better approach:

```java
ListNode current = head;

while (current != null) {
    System.out.println(current.val);
    current = current.next;
}
```

Now `head` remains safe.

---

## Basic Traversal Template

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

---

## Step-by-Step Logic

```txt
1. Start from head
2. Store head in current
3. While current is not null
4. Process current node
5. Move current to current.next
6. Stop when current becomes null
```

---

## Traversal Dry Run

Linked list:

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

Dry run:

| Step | current points to | Printed | Move current to |
|---:|---|---:|---|
| 1 | 10 | 10 | 20 |
| 2 | 20 | 20 | 30 |
| 3 | 30 | 30 | null |
| 4 | null | loop stops | end |

Output:

```txt
10
20
30
```

---

## Why Condition is `current != null`

We use:

```java
while (current != null)
```

because `null` means there is no node left.

If we write:

```java
System.out.println(current.val);
```

when `current` is `null`, Java will throw:

```txt
NullPointerException
```

So always check before accessing:

```txt
current.val
current.next
```

---

## Operation 1: Print All Nodes

Problem:

```txt
Given the head of a linked list, print all node values.
```

Solution:

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

## Operation 2: Find Length

Problem:

```txt
Given the head of a linked list, return the number of nodes.
```

Logic:

```txt
start count = 0
visit each node
increase count by 1
return count
```

Code:

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

Dry run:

```txt
head → 5 → 10 → 15 → null
```

| Step | current | length before | length after |
|---:|---:|---:|---:|
| 1 | 5 | 0 | 1 |
| 2 | 10 | 1 | 2 |
| 3 | 15 | 2 | 3 |
| 4 | null | 3 | stop |

Final answer:

```txt
3
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

## Operation 3: Search a Value

Problem:

```txt
Given the head of a linked list and a target value, return true if target exists.
```

Logic:

```txt
start from head
check current value
if value equals target, return true
otherwise move forward
if traversal ends, return false
```

Code:

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

Dry run:

```txt
head → 4 → 8 → 12 → 16 → null
target = 12
```

| Step | current value | Is target found? |
|---:|---:|---|
| 1 | 4 | No |
| 2 | 8 | No |
| 3 | 12 | Yes |

Return:

```txt
true
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

## Operation 4: Count Occurrences

Problem:

```txt
Count how many times target appears in the linked list.
```

Example:

```txt
head → 2 → 5 → 2 → 7 → 2 → null
target = 2
```

Answer:

```txt
3
```

Code:

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

Time complexity:

```txt
O(n)
```

Space complexity:

```txt
O(1)
```

---

## Operation 5: Find Sum of Nodes

Problem:

```txt
Return the sum of all node values.
```

Example:

```txt
head → 10 → 20 → 30 → null
```

Answer:

```txt
60
```

Code:

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

Time complexity:

```txt
O(n)
```

Space complexity:

```txt
O(1)
```

---

## Operation 6: Find Maximum Value

Problem:

```txt
Return the maximum value in the linked list.
```

Assumption:

```txt
The list is not empty.
```

Code:

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

For empty list, handle separately:

```java
if (head == null) {
    throw new IllegalArgumentException("List is empty");
}
```

---

## Operation 7: Find Minimum Value

Problem:

```txt
Return the minimum value in the linked list.
```

Code:

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

Time complexity:

```txt
O(n)
```

Space complexity:

```txt
O(1)
```

---

## Operation 8: Find Position of Target

Problem:

```txt
Return the first position where target appears.
```

Use 0-based indexing.

Example:

```txt
head → 10 → 20 → 30 → 40 → null
target = 30
```

Answer:

```txt
2
```

Code:

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

Return `-1` if target is not found.

---

## Empty List Case

If:

```txt
head → null
```

Then:

| Operation | Result |
|---|---|
| Print | Nothing printed |
| Length | 0 |
| Search | false |
| Count occurrences | 0 |
| Sum | 0 |
| Find max/min | Invalid unless handled |

---

## Single Node Case

If:

```txt
head → 10 → null
```

Then:

| Operation | Result |
|---|---|
| Print | 10 |
| Length | 1 |
| Search 10 | true |
| Search 20 | false |
| Sum | 10 |
| Max | 10 |
| Min | 10 |

---

## Pattern Complexity

For traversal-based operations:

```txt
Time Complexity: O(n)
Space Complexity: O(1)
```

Why?

```txt
Every node is visited at most once.
Only a few variables are used.
```

Variables may include:

```txt
current
count
sum
position
maxValue
minValue
```

These do not grow with input size.

---

## When Traversal is Enough

Traversal is enough when the problem only asks to:

```txt
read nodes
count nodes
search values
calculate something
find simple information
```

Traversal is not enough when the problem asks to:

```txt
delete nodes
reverse links
detect cycle
find middle efficiently
merge lists
reorder list
clone random pointer list
```

Those problems need additional patterns.

---

## Common Mistakes

| Mistake | Why it is wrong | Correct approach |
|---|---|---|
| Moving head directly | Original list start may be lost | Use current |
| Accessing current.val when current is null | Causes NullPointerException | Check current != null |
| Forgetting to move current | Causes infinite loop | Always do current = current.next |
| Returning false too early in search | Stops after first non-match | Return false only after loop |
| Initializing max/min incorrectly | Fails for negative values | Start with head.val |
| Ignoring empty list | Code may fail | Check head == null |

---

## Search Mistake Example

Wrong:

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

Problem:

```txt
This checks only the first node.
```

Correct:

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

## Infinite Loop Mistake

Wrong:

```java
ListNode current = head;

while (current != null) {
    System.out.println(current.val);
}
```

Problem:

```txt
current is never moved.
The loop never ends.
```

Correct:

```java
ListNode current = head;

while (current != null) {
    System.out.println(current.val);
    current = current.next;
}
```

---

## Pattern Recognition Summary

Use Pattern 01 when you see:

```txt
count
length
search
exists
print
sum
maximum
minimum
occurrence
position
visit all nodes
```

Main pointer:

```txt
current
```

Main loop:

```java
while (current != null)
```

Main movement:

```java
current = current.next;
```

---

## Final Revision

```txt
Traversal = move from head to null
Search = traversal with condition
Length = traversal with counter
Sum = traversal with addition
Max/Min = traversal with comparison
Position = traversal with index counter
```

---

## Day 3 Learning Goal

After completing this pattern, you should be able to:

```txt
traverse a linked list safely
print all values
find length
search a target
count occurrences
find sum
find max and min
find target position
handle empty and single-node cases
avoid infinite loops
avoid NullPointerException
```

---

## Final Checklist

| Skill | Status |
|---|---|
| Understand traversal pattern | ✅ |
| Understand current pointer | ✅ |
| Print linked list | ✅ |
| Find length | ✅ |
| Search target | ✅ |
| Count occurrences | ✅ |
| Find sum | ✅ |
| Find max/min | ✅ |
| Find position | ✅ |
| Handle empty list | ✅ |
| Handle single-node list | ✅ |
| Avoid common mistakes | ✅ |
