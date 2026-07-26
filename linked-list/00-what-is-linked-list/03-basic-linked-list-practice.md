# Basic Linked List Practice

This file contains beginner-friendly practice for Day 1 of Linked List.

The goal is not to solve advanced linked list problems yet.

The goal is to build clarity about:

```txt
node
head
next
null
traversal
basic pointer movement
basic complexity
```

---

## How to Practice This Day

For every linked list, write:

```txt
Head:
Nodes:
Tail:
Where is null?
Traversal order:
Number of nodes:
Time complexity:
Space complexity:
```

This builds the habit of dry running linked list problems visually.

---

## Practice 1: Identify Linked List Parts

Given:

```txt
head → 10 → 20 → 30 → null
```

Fill:

```txt
Head:
Nodes:
Tail:
Where is null?
Traversal order:
Number of nodes:
```

Answer:

```txt
Head: 10
Nodes: 10, 20, 30
Tail: 30
Where is null? After 30
Traversal order: 10, 20, 30
Number of nodes: 3
```

---

## Practice 2: Empty Linked List

Given:

```txt
head → null
```

Answer these:

```txt
Is the list empty?
Number of nodes:
Traversal output:
```

Answer:

```txt
Is the list empty? Yes
Number of nodes: 0
Traversal output: Nothing will be printed
```

---

## Practice 3: Single Node Linked List

Given:

```txt
head → 50 → null
```

Answer:

```txt
Head:
Tail:
Number of nodes:
Is head also tail?
Where is null?
```

Answer:

```txt
Head: 50
Tail: 50
Number of nodes: 1
Is head also tail? Yes
Where is null? After 50
```

---

## Practice 4: Draw the Connections

Given nodes:

```java
ListNode a = new ListNode(5);
ListNode b = new ListNode(10);
ListNode c = new ListNode(15);

a.next = b;
b.next = c;
c.next = null;
```

Draw the linked list.

Answer:

```txt
a/head → 5 → 10 → 15 → null
```

---

## Practice 5: Find the Output

Code:

```java
ListNode current = head;

while (current != null) {
    System.out.print(current.val + " ");
    current = current.next;
}
```

Linked list:

```txt
head → 1 → 2 → 3 → 4 → null
```

Output:

```txt
1 2 3 4
```

---

## Practice 6: Dry Run Traversal

Linked list:

```txt
head → 7 → 14 → 21 → null
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

| Step | current points to | Printed | Next current |
|---:|---|---:|---|
| 1 | 7 | 7 | 14 |
| 2 | 14 | 14 | 21 |
| 3 | 21 | 21 | null |
| 4 | null | loop stops | end |

Output:

```txt
7
14
21
```

---

## Practice 7: Count Nodes Manually

Given:

```txt
head → 11 → 22 → 33 → 44 → 55 → null
```

Find length.

Answer:

```txt
5
```

Reason:

```txt
There are 5 nodes: 11, 22, 33, 44, 55
```

---

## Practice 8: Fill the Java Node Class

Complete the blanks:

```java
class ListNode {
    int val;
    ListNode next;

    ListNode(int val) {
        this.val = _____;
        this.next = _____;
    }
}
```

Answer:

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

## Practice 9: Create a Linked List Manually

Create this linked list:

```txt
head → 100 → 200 → 300 → null
```

Answer:

```java
ListNode first = new ListNode(100);
ListNode second = new ListNode(200);
ListNode third = new ListNode(300);

first.next = second;
second.next = third;
third.next = null;

ListNode head = first;
```

---

## Practice 10: Identify the Mistake

Code:

```java
while (head != null) {
    System.out.println(head.val);
    head = head.next;
}
```

Question:

```txt
What is the issue with this code?
```

Answer:

```txt
The code moves the head pointer directly.

After the loop ends, head becomes null and the original starting reference is lost.

Use a temporary pointer instead.
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

## Practice 11: NullPointerException Check

Code:

```java
ListNode current = null;
System.out.println(current.val);
```

Question:

```txt
What will happen?
```

Answer:

```txt
Java will throw NullPointerException because current is null and we are trying to access current.val.
```

Correct thinking:

```txt
Always check current != null before accessing current.val.
```

---

## Practice 12: Find Complexity

Code:

```java
ListNode current = head;

while (current != null) {
    current = current.next;
}
```

Answer:

```txt
Time Complexity: O(n)
Space Complexity: O(1)
```

Reason:

```txt
Every node is visited once.
Only one extra pointer is used.
```

---

## Practice 13: Insert at Head Dry Run

Before:

```txt
head → 10 → 20 → 30 → null
```

Insert:

```txt
5
```

Steps:

```java
ListNode newNode = new ListNode(5);
newNode.next = head;
head = newNode;
```

After:

```txt
head → 5 → 10 → 20 → 30 → null
```

Time complexity:

```txt
O(1)
```

---

## Practice 14: Delete Head Dry Run

Before:

```txt
head → 10 → 20 → 30 → null
```

Code:

```java
head = head.next;
```

After:

```txt
head → 20 → 30 → null
```

Time complexity:

```txt
O(1)
```

---

## Practice 15: Search Dry Run

Linked list:

```txt
head → 4 → 8 → 12 → 16 → null
```

Target:

```txt
12
```

Dry run:

| Step | current value | Is target found? |
|---:|---:|---|
| 1 | 4 | No |
| 2 | 8 | No |
| 3 | 12 | Yes |

Answer:

```txt
Target found.
Time complexity: O(n)
Space complexity: O(1)
```

---

## Practice 16: Search Target Not Present

Linked list:

```txt
head → 4 → 8 → 12 → 16 → null
```

Target:

```txt
20
```

Dry run:

```txt
4 → 8 → 12 → 16 → null
```

Answer:

```txt
Target not found.
Time complexity: O(n)
Space complexity: O(1)
```

---

## Practice 17: Concept MCQs

### Q1. What does `head` store?

```txt
A. Last node
B. First node reference
C. Number of nodes
D. Always null
```

Answer:

```txt
B. First node reference
```

---

### Q2. What does `next` store?

```txt
A. Previous node value
B. Index of current node
C. Reference to next node
D. Length of list
```

Answer:

```txt
C. Reference to next node
```

---

### Q3. What does `null` mean?

```txt
A. List is sorted
B. List has duplicates
C. End of list
D. List has cycle
```

Answer:

```txt
C. End of list
```

---

### Q4. Why is linked list access O(n)?

```txt
A. Because Java is slow
B. Because linked list has no direct index jump
C. Because values are unsorted
D. Because values are private
```

Answer:

```txt
B. Because linked list has no direct index jump
```

---

### Q5. What should be used for traversal?

```txt
A. A temporary current pointer
B. Always move head directly
C. Array index
D. Random access
```

Answer:

```txt
A. A temporary current pointer
```

---

## Practice 18: Write Traversal Function

Task:

```txt
Write a function to print all nodes of a linked list.
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

## Practice 19: Write Length Function

Task:

```txt
Write a function to find the length of a linked list.
```

Solution:

```java
class Solution {
    public int findLength(ListNode head) {
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
O(n)
```

Space complexity:

```txt
O(1)
```

---

## Practice 20: Write Search Function

Task:

```txt
Return true if target exists in linked list.
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

Time complexity:

```txt
O(n)
```

Space complexity:

```txt
O(1)
```

---

## Practice 21: Edge Case Testing

Test your functions on:

```txt
head = null
head = 10 → null
head = 10 → 20 → null
head = 10 → 20 → 30 → null
```

Check:

```txt
Does traversal stop correctly?
Does length return correct value?
Does search handle missing target?
Does code avoid NullPointerException?
```

---

## Common Mistakes to Avoid

| Mistake | Correct Thinking |
|---|---|
| Moving head directly | Use current pointer |
| Accessing current.val without null check | Check current != null |
| Thinking linked list has index access | It moves node by node |
| Forgetting empty list case | Check head == null |
| Confusing node value and node reference | Track both separately |
| Skipping dry run | Always trace pointer movement |

---

## Day 1 Final Revision

```txt
Linked List = nodes connected by references
Node = value + next
Head = first node
Tail = last node
Null = end
Traversal = node-by-node movement
Access = O(n)
Search = O(n)
Insert at head = O(1)
Delete head = O(1)
```

---

## Day 1 Completion Checklist

| Task | Status |
|---|---|
| Understand linked list meaning | ✅ |
| Understand node structure | ✅ |
| Understand head pointer | ✅ |
| Understand next pointer | ✅ |
| Understand null ending | ✅ |
| Understand empty list | ✅ |
| Understand single node list | ✅ |
| Dry run traversal manually | ✅ |
| Understand basic complexity | ✅ |
| Write ListNode class | ✅ |
| Write traversal code | ✅ |
| Write length code | ✅ |
| Write search code | ✅ |
| Identify common mistakes | ✅ |
