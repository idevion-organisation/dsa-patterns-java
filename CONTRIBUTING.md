# Contributing to DSA Patterns Java

Thank you for your interest in contributing to **DSA Patterns Java** by **Idevion**.

This repository is built to help students learn Data Structures and Algorithms in Java using a **pattern-based learning approach**.

The goal is not to memorize solutions.

The goal is to help learners understand:

```txt
how to recognize a pattern
when to use a pattern
how the logic works
how to dry run the solution
how to write clean Java code
how to avoid common mistakes
```

---

## Who Can Contribute?

Anyone can contribute, especially:

- Students learning DSA
- Beginners practicing Java
- Developers who want to improve explanations
- Open-source contributors
- Mentors who want to add better dry runs or practice problems

You do not need to be an expert to contribute.

Even small improvements are valuable.

---

## What You Can Contribute

You can contribute by:

- Fixing spelling or grammar mistakes
- Improving explanations
- Adding better dry runs
- Adding missing edge cases
- Improving Java templates
- Adding beginner-friendly examples
- Adding practice problems
- Improving folder navigation
- Improving README sections
- Reporting mistakes through issues

---

## Repository Learning Structure

Each topic module follows a pattern-wise structure.

Example:

```txt
arrays/
linked-list/
stack/
queue/
strings/
recursion/
trees/
graphs/
dynamic-programming/
```

Each module contains learning days and pattern folders.

---

## Standard Folder Format

Every learning day or pattern folder should follow this structure wherever applicable:

```txt
folder-name/
├── 01-concept-or-pattern-name.md
├── 02-pattern-name-templates-java.md
└── 03-day-N-practice.md
```

Example:

```txt
linked-list/
└── 08-pattern-07-linked-list-reversal/
    ├── 01-pattern-07-linked-list-reversal.md
    ├── 02-linked-list-reversal-templates-java.md
    └── 03-day-9-practice.md
```

---

## File 1: Concept or Pattern Explanation

The first file should explain the concept or pattern clearly.

It should usually include:

```txt
Meaning
Why this concept/pattern matters
When to use it
How to recognize the pattern
Pattern signal
Core logic
Step-by-step explanation
Dry run
Java implementation
Line-by-line explanation
Time complexity
Space complexity
Common mistakes
Final checklist
```

Keep the explanation beginner-friendly.

Avoid jumping directly to code.

---

## File 2: Java Templates

The second file should contain reusable Java templates.

It should usually include:

```txt
Basic template
Optimized template
Edge-case handling template
Helper method template if needed
Reusable code structure
Time and space complexity
```

Rules for Java templates:

- Use Java only
- Keep code clean and readable
- Avoid unnecessary advanced syntax
- Add meaningful variable names
- Prefer beginner-friendly logic
- Mention complexity after the code

---

## File 3: Practice File

The third file should help learners practice the pattern.

It should usually include:

```txt
Practice method
Manual dry-run problems
Beginner-level problems
LeetCode or similar practice list
Pattern identification questions
Common mistakes
Answer key
Completion checklist
```

The practice file should help students test whether they can identify and apply the pattern.

---

## Java Code Guidelines

Please follow these rules while contributing Java code:

```txt
Use class Solution where problem-style code is required
Use clear method names
Use meaningful variable names
Avoid unnecessary comments
Keep logic beginner-friendly
Mention time complexity
Mention space complexity
Handle edge cases
```

Good example:

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

Avoid unclear code like:

```java
class Solution {
    public int f(ListNode h) {
        int c = 0;
        while (h != null) {
            c++;
            h = h.next;
        }
        return c;
    }
}
```

---

## Content Quality Rules

Before submitting content, check:

```txt
Is the explanation beginner-friendly?
Is the pattern clearly named?
Is the pattern signal included?
Is there a dry run?
Is Java code included?
Is complexity mentioned?
Are common mistakes added?
Is the practice section useful?
```

---

## Do Not Add Fake Patterns

This repository follows a clean pattern-based structure.

Do not create unnecessary pattern folders just because a problem is popular.

For example, in Linked List, these should not be separate main pattern folders:

```txt
Middle of Linked List
Remove Nth Node From End
Delete Node
Odd Even Linked List
Rotate List
Remove Duplicates
Swap Nodes
Partition List
```

These belong inside larger patterns such as:

```txt
Fast and Slow Pointers
Two Pointers Gap Pattern
Pointer Rewiring
Dummy Node
List Weaving and Reordering
```

---

## Current Module Standard

The Array module is the reference structure.

Future modules should follow the same quality and format.

Current module roadmap:

```txt
v1.0 → Array Patterns
v2.0 → Linked List Patterns
v3.0 → Stack Patterns
v4.0 → Queue Patterns
v5.0 → String Patterns
v6.0 → Recursion Patterns
v7.0 → Tree Patterns
v8.0 → Graph Patterns
v9.0 → Dynamic Programming Patterns
```

---

## How to Contribute

### Step 1: Pick an Issue

Go to the Issues tab and pick an issue related to:

```txt
documentation
beginner-friendly
good first issue
enhancement
roadmap
```

### Step 2: Comment on the Issue

Comment that you want to work on it.

Example:

```txt
I would like to work on this issue.
```

### Step 3: Fork the Repository

Fork the repository to your GitHub account.

### Step 4: Create a Branch

Use a meaningful branch name.

Example:

```txt
add-linked-list-traversal-pattern
```

### Step 5: Make Your Changes

Follow the folder and file structure properly.

### Step 6: Create a Pull Request

Open a pull request with a clear title.

Good pull request title:

```txt
Add Linked List Traversal Pattern
```

Bad pull request title:

```txt
Update files
```

---

## Pull Request Checklist

Before opening a pull request, make sure:

```txt
The folder name is correct
The file names are correct
The explanation is beginner-friendly
The Java code is tested manually
The dry run is included
The complexity is included
The practice file is included
No unrelated files are changed
```

---

## Commit Message Guidelines

Use clear commit messages.

Good examples:

```txt
Add linked list traversal pattern
Add Java templates for dummy node pattern
Fix array prefix sum dry run
Improve sliding window practice problems
```

Avoid unclear messages:

```txt
changes
update
fix
new file
final
```

---

## Issue Guidelines

When creating an issue, explain clearly:

```txt
What needs to be improved
Where the problem exists
What change is expected
```

Good issue title:

```txt
Improve dry run for variable size sliding window
```

Bad issue title:

```txt
Problem
```

---

## Learning Philosophy

This repository follows one simple idea:

```txt
Do not memorize every problem.
Learn the pattern behind the problem.
```

Every contribution should support this goal.

---

## Community Note

Be respectful and helpful.

This project is created for students and beginners, so explanations should be simple, practical, and encouraging.

Thank you for helping improve **DSA Patterns Java** by **Idevion**.
