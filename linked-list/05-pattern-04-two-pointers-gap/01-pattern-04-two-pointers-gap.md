# Pattern 04: Two Pointers Gap Pattern

The Two Pointers Gap Pattern is used when we need to maintain a fixed distance between two pointers in a linked list.

This pattern is very useful when the problem talks about:

```txt
nth node from end
kth node from end
remove nth node from end
fixed distance between two nodes
align two linked lists by length difference
```

---

## Why This Pattern Matters

In arrays, we can directly access an element from the end using index calculations.

Example:

```java
arr[arr.length - n]
```

But in linked list, we cannot jump directly to any index.

We only have:

```txt
head
next reference
```

So to find something from the end, we use two pointers with a fixed gap.

---

## Pattern Name

```txt
Two Pointers Gap Pattern
```

Also known as:

```txt
Fixed Gap Pointer Pattern
Nth From End Pattern
Kth From End Pattern
Lead and Follow Pointer Pattern
```

---

## Core Idea

Use two pointers:

```txt
fast
slow
```

First, move `fast` ahead by `n` steps.

Then move both `fast` and `slow` one step at a time.

When `fast` reaches the end, `slow` will be at the required node.

---

## Basic Visual

Linked list:

```txt
head → 10 → 20 → 30 → 40 → 50 → null
```

Find 2nd node from end.

Move `fast` 2 steps ahead:

```txt
slow
 |
 v
10 → 20 → 30 → 40 → 50 → null
          ^
          |
        fast
```

Now move both together until `fast` reaches null.

Final:

```txt
10 → 20 → 30 → 40 → 50 → null
               ^         ^
               |         |
             slow       fast(null)
```

`slow` points to:

```txt
40
```

So 2nd node from end is:

```txt
40
```

---

## Pattern Signal

Use this pattern when the problem says:

```txt
nth node from end
kth node from end
remove nth node from end
delete kth node from end
find node from last
maintain distance
fixed gap
two pointers with distance
align two lists by length difference
```

Common problem statements:

```txt
Find the nth node from the end of a linked list.
Remove the nth node from the end of a linked list.
Return the kth node from the last.
Delete the kth node from the end.
Find intersection after aligning two lists by length.
```

---

## Difference Between Gap Pointers and Fast-Slow Pointers

Many beginners confuse these two.

| Pattern | Pointer Movement | Used For |
|---|---|---|
| Two Pointers Gap | Fast is moved fixed steps ahead, then both move one step | nth from end, remove nth from end |
| Fast and Slow | Slow moves 1 step, fast moves 2 steps | middle node, cycle detection |

In this pattern:

```txt
fast does not always move 2 steps.
```

Instead:

```txt
fast starts n steps ahead of slow.
```

---

## Main Pointers Used

| Pointer | Purpose |
|---|---|
| `fast` | Moves ahead first to create gap |
| `slow` | Follows behind fast |
| `dummy` | Helps when deletion can affect head |
| `head` | Starting node of original list |

---

## Standard Gap Formula

For finding nth node from end:

```txt
Move fast n steps ahead.
Move slow and fast together.
When fast reaches null, slow is nth node from end.
```

For removing nth node from end:

```txt
Use dummy.
Move fast n + 1 steps ahead from dummy.
Move slow and fast together.
When fast reaches null, slow is before the node to delete.
Delete slow.next.
```

---

## Operation 1: Find Nth Node From End

Problem:

```txt
Given the head of a linked list and an integer n, return the nth node from the end.
```

Example:

```txt
head → 10 → 20 → 30 → 40 → 50 → null
n = 2
```

Output:

```txt
40
```

---

## Logic

```txt
1. Set slow = head.
2. Set fast = head.
3. Move fast n steps ahead.
4. Move slow and fast together until fast becomes null.
5. Return slow.
```

---

## Java Code

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

---

## Dry Run: Find 2nd Node From End

Input:

```txt
head → 10 → 20 → 30 → 40 → 50 → null
n = 2
```

Initial:

```txt
slow = 10
fast = 10
```

Move `fast` 2 steps ahead:

| Step | fast moves to |
|---:|---|
| 1 | 20 |
| 2 | 30 |

Now:

```txt
slow = 10
fast = 30
```

Move both together:

| Step | slow | fast |
|---:|---:|---:|
| 1 | 20 | 40 |
| 2 | 30 | 50 |
| 3 | 40 | null |

Stop when:

```txt
fast = null
```

Answer:

```txt
slow = 40
```

---

## Why This Works

After moving `fast` n steps ahead, there is a gap of `n` nodes between `slow` and `fast`.

When `fast` reaches null, `slow` has exactly `n` nodes after it including itself.

So `slow` is the nth node from the end.

---

## Operation 2: Find Kth Node From End

This is the same as nth node from end.

Problem:

```txt
Return kth node from the end of the linked list.
```

Code:

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

Time complexity:

```txt
O(n)
```

Space complexity:

```txt
O(1)
```

---

## Operation 3: Remove Nth Node From End

Problem:

```txt
Given the head of a linked list, remove the nth node from the end and return the new head.
```

Example:

```txt
Input:
head → 10 → 20 → 30 → 40 → 50 → null
n = 2

Output:
head → 10 → 20 → 30 → 50 → null
```

The 2nd node from end is:

```txt
40
```

So remove `40`.

---

## Why Dummy Node Is Needed

When removing nth node from end, the node to remove can be the head.

Example:

```txt
head → 10 → 20 → 30 → null
n = 3
```

The 3rd node from end is:

```txt
10
```

So head changes.

To handle this safely, use a dummy node:

```txt
dummy → 10 → 20 → 30 → null
```

At the end, return:

```java
return dummy.next;
```

---

## Remove Nth From End Logic

```txt
1. Create dummy node.
2. Connect dummy.next = head.
3. Set fast = dummy and slow = dummy.
4. Move fast n + 1 steps ahead.
5. Move fast and slow together until fast becomes null.
6. Now slow is before the node to delete.
7. Delete slow.next.
8. Return dummy.next.
```

---

## Java Code

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

---

## Why Move `fast` n + 1 Steps?

For deletion, we do not want `slow` to stop at the target node.

We want `slow` to stop before the target node.

Because deletion needs:

```java
slow.next = slow.next.next;
```

That is why we create one extra gap using dummy.

---

## Dry Run: Remove 2nd Node From End

Input:

```txt
dummy → 10 → 20 → 30 → 40 → 50 → null
n = 2
```

Initial:

```txt
slow = dummy
fast = dummy
```

Move `fast` `n + 1 = 3` steps:

| Step | fast moves to |
|---:|---|
| 1 | 10 |
| 2 | 20 |
| 3 | 30 |

Now:

```txt
slow = dummy
fast = 30
```

Move both:

| Step | slow | fast |
|---:|---|---|
| 1 | 10 | 40 |
| 2 | 20 | 50 |
| 3 | 30 | null |

Now:

```txt
slow = 30
slow.next = 40
```

Delete:

```java
slow.next = slow.next.next;
```

Result:

```txt
10 → 20 → 30 → 50 → null
```

---

## Dry Run: Remove Head Using Gap Pattern

Input:

```txt
head → 10 → 20 → 30 → null
n = 3
```

With dummy:

```txt
dummy → 10 → 20 → 30 → null
```

Move `fast` `n + 1 = 4` steps:

| Step | fast moves to |
|---:|---|
| 1 | 10 |
| 2 | 20 |
| 3 | 30 |
| 4 | null |

Since `fast` is already null, slow stays at dummy.

Now:

```txt
slow = dummy
slow.next = 10
```

Delete:

```java
slow.next = slow.next.next;
```

Result:

```txt
20 → 30 → null
```

Return:

```java
dummy.next
```

---

## Operation 4: Delete Kth Node From End

This is the same as removing nth node from end.

Problem:

```txt
Delete kth node from the end of linked list.
```

Code:

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

## Operation 5: Find Node Before Nth Node From End

Sometimes we need the node before the nth node from end.

This is useful for deletion.

Example:

```txt
head → 10 → 20 → 30 → 40 → 50 → null
n = 2
```

Nth node from end:

```txt
40
```

Node before it:

```txt
30
```

Code:

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

---

## Operation 6: Check If Linked List Has At Least K Nodes

Gap pointer setup often starts by moving `fast` k steps.

If `fast` becomes null before completing k steps, the list has fewer than k nodes.

Code:

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
head → 10 → 20 → 30 → null
k = 4
```

Answer:

```txt
false
```

---

## Operation 7: Find Node After K Steps

Problem:

```txt
Given a node, return the node after k steps.
```

Example:

```txt
10 → 20 → 30 → 40 → null
k = 2
```

Starting from `10`, after 2 steps:

```txt
30
```

Code:

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

This is a helper used in many gap-based problems.

---

## Operation 8: Align Two Lists by Length Difference

Sometimes two linked lists have different lengths.

To compare them fairly, move the pointer of the longer list ahead by the length difference.

Example:

```txt
List A:
1 → 2 → 3 → 4 → 5 → null

List B:
9 → 8 → 4 → 5 → null
```

Length difference:

```txt
5 - 4 = 1
```

Move pointer of longer list one step ahead.

This makes both remaining paths equal in length.

---

## Why This Is a Gap Pattern

The longer list pointer starts ahead by the gap:

```txt
gap = abs(lengthA - lengthB)
```

Then both pointers move together.

This idea is useful in intersection problems.

The full intersection pattern will be covered later.

---

## Code: Move Longer Pointer by Gap

```java
class Solution {
    public ListNode moveLongerByGap(ListNode longerHead, int gap) {
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

---

## Gap Pattern vs Length-Based Approach

To find nth node from end, one approach is:

```txt
1. Find length
2. Calculate position from start
3. Traverse again
```

This needs two passes.

Gap pointer approach:

```txt
1. Move fast n steps
2. Move slow and fast together
```

This finds the answer in one pass.

Both are:

```txt
O(n)
```

But gap pattern is more elegant and interview-friendly.

---

## Complexity

For most gap pointer problems:

```txt
Time Complexity: O(n)
Space Complexity: O(1)
```

Why?

```txt
Each pointer moves through the list at most once.
Only a few pointer variables are used.
```

---

## Complexity Summary

| Operation | Time | Space |
|---|---:|---:|
| Find nth node from end | O(n) | O(1) |
| Find kth node from end | O(n) | O(1) |
| Remove nth node from end | O(n) | O(1) |
| Delete kth node from end | O(n) | O(1) |
| Find previous of nth from end | O(n) | O(1) |
| Check at least k nodes | O(k) | O(1) |
| Move k steps | O(k) | O(1) |
| Align two lists by gap | O(n + m) | O(1) |

---

## Common Mistakes

| Mistake | Why it is wrong | Correct approach |
|---|---|---|
| Moving fast wrong number of steps | Slow reaches wrong node | Count gap carefully |
| Not handling `n <= 0` | Invalid input may break logic | Return safely |
| Not checking fast during initial movement | NullPointerException | Check fast before moving |
| Removing nth without dummy | Head deletion becomes messy | Use dummy |
| Moving slow before creating full gap | Gap becomes incorrect | Move fast first |
| Returning slow for deletion | Need to delete slow.next | Return dummy.next |
| Confusing gap with fast-slow pattern | Wrong movement logic | Gap means fixed distance |

---

## Mistake Example 1: Returning Wrong Node

For removing nth node from end, this is wrong:

```java
return slow;
```

Problem:

```txt
The task asks to return the updated head, not the previous node.
```

Correct:

```java
return dummy.next;
```

---

## Mistake Example 2: Not Using Dummy

Wrong for head deletion:

```java
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode fast = head;
        ListNode slow = head;

        for (int i = 0; i < n; i++) {
            fast = fast.next;
        }

        while (fast.next != null) {
            fast = fast.next;
            slow = slow.next;
        }

        slow.next = slow.next.next;

        return head;
    }
}
```

Problem:

```txt
This can fail when the node to remove is the head.
```

Better:

```txt
Use dummy node.
```

---

## Mistake Example 3: Confusing `fast != null` and `fast.next != null`

For finding nth from end:

```java
while (fast != null)
```

is used after creating the gap.

For stopping before the last node, sometimes:

```java
while (fast.next != null)
```

is used.

Use the condition based on what the problem needs.

For this pattern:

```txt
Finding nth from end → stop when fast == null
Deleting nth from end using dummy → stop when fast == null
```

---

## Pattern Recognition Summary

Use Two Pointers Gap when you see:

```txt
nth from end
kth from end
remove from end
delete from end
fixed distance
length difference
move one pointer ahead first
```

Main setup:

```java
ListNode fast = head;
ListNode slow = head;
```

For deletion:

```java
ListNode dummy = new ListNode(0);
dummy.next = head;

ListNode fast = dummy;
ListNode slow = dummy;
```

---

## Day 6 Learning Goal

After completing this pattern, you should be able to:

```txt
understand fixed gap pointer movement
find nth node from end
find kth node from end
remove nth node from end
delete kth node from end
find previous node before target from end
use dummy node with gap pointers
handle head deletion safely
understand gap vs fast-slow difference
avoid off-by-one pointer mistakes
```

---

## Final Revision

```txt
Two Pointers Gap = fixed distance between fast and slow

Find nth from end:
move fast n steps
move fast and slow together
when fast is null, slow is answer

Remove nth from end:
use dummy
move fast n + 1 steps from dummy
move fast and slow together
slow stops before target
delete slow.next
return dummy.next
```

---

## Final Checklist

| Skill | Status |
|---|---|
| Understand gap pointer idea | ✅ |
| Understand fast and slow roles | ✅ |
| Find nth node from end | ✅ |
| Find kth node from end | ✅ |
| Remove nth node from end | ✅ |
| Delete kth node from end | ✅ |
| Use dummy for deletion | ✅ |
| Handle head deletion | ✅ |
| Handle invalid n | ✅ |
| Understand gap vs fast-slow | ✅ |
| Avoid off-by-one mistakes | ✅ |
| Understand complexity | ✅ |
