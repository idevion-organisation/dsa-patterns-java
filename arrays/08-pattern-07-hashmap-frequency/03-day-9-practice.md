# Day 9 Practice: Pattern 07 HashMap Frequency

Today's goal is to master the **HashMap Frequency Pattern**.

HashMap is used when we need to count occurrences, track frequency, or store value-index relationships.

---

## Practice Method

For every problem, write:

```txt
Given:
Asked:
Need frequency or index?
What is key?
What is value?
Pattern:
Return:
Time Complexity:
Space Complexity:
```

Example:

```txt
Problem: Count frequency of each element

Given: integer array
Asked: frequency of every element
Need frequency or index? frequency
Key: array element
Value: occurrence count
Pattern: HashMap Frequency
Return: frequency map
Time: O(n) average
Space: O(n)
```

---

## Manual Practice Problems

### 1. Count Frequency

```txt
Input: nums = [2, 3, 2, 4, 3, 2]

Output:
2 → 3
3 → 2
4 → 1
```

Think:

```txt
key = number
value = frequency
```

---

### 2. Frequency of Target

```txt
Input: nums = [1, 2, 2, 3, 2], target = 2
Output: 3
```

Think:

```txt
Build frequency map, then get target count.
```

---

### 3. Target Not Present

```txt
Input: nums = [1, 2, 3], target = 5
Output: 0
```

Think:

```txt
Use getOrDefault(target, 0).
```

---

### 4. Most Frequent Element

```txt
Input: nums = [1, 3, 2, 3, 4, 3]
Output: 3
```

Think:

```txt
Build frequency map, then find maximum count.
```

---

### 5. First Unique Element

```txt
Input: nums = [4, 5, 1, 2, 1, 5]
Output: 4
```

Think:

```txt
Build frequency map.
Scan original array again.
Return first element with frequency 1.
```

---

### 6. Majority Element

```txt
Input: nums = [3, 2, 3]
Output: 3
```

Think:

```txt
Return element with count greater than n / 2.
```

---

### 7. Two Sum

```txt
Input: nums = [2, 7, 11, 15], target = 9
Output: [0, 1]
```

Think:

```txt
Need = target - nums[i]
Map stores value → index.
```

---

### 8. Intersection With Duplicates

```txt
Input:
nums1 = [1, 2, 2, 3]
nums2 = [2, 2, 4]

Output: [2, 2]
```

Think:

```txt
Frequency of nums1 controls how many times each value can be used.
```

---

## Dry Run Practice

Dry run frequency map:

```txt
nums = [2, 3, 2, 4, 3, 2]
```

Fill this table:

| Step | i | nums[i] | Old Count | New Count | Map |
|---:|---:|---:|---:|---:|---|
| 1 |  |  |  |  |  |
| 2 |  |  |  |  |  |
| 3 |  |  |  |  |  |
| 4 |  |  |  |  |  |
| 5 |  |  |  |  |  |
| 6 |  |  |  |  |  |

---

## Completed Dry Run Answer

```txt
nums = [2, 3, 2, 4, 3, 2]
```

| Step | i | nums[i] | Old Count | New Count | Map |
|---:|---:|---:|---:|---:|---|
| 1 | 0 | 2 | 0 | 1 | {2=1} |
| 2 | 1 | 3 | 0 | 1 | {2=1, 3=1} |
| 3 | 2 | 2 | 1 | 2 | {2=2, 3=1} |
| 4 | 3 | 4 | 0 | 1 | {2=2, 3=1, 4=1} |
| 5 | 4 | 3 | 1 | 2 | {2=2, 3=2, 4=1} |
| 6 | 5 | 2 | 2 | 3 | {2=3, 3=2, 4=1} |

Final:

```txt
2 → 3
3 → 2
4 → 1
```

---

## Common Mistake Practice

### Mistake 1

Find the error:

```java
map.put(num, map.get(num) + 1);
```

Problem:

```txt
If num is not present, map.get(num) gives null.
```

Correct:

```java
map.put(num, map.getOrDefault(num, 0) + 1);
```

---

### Mistake 2

Find the error:

```java
HashMap<Integer, Integer> map = new HashMap<>();
```

Problem:

```txt
Missing import statement.
```

Correct:

```java
import java.util.HashMap;
```

---

### Mistake 3

Find the issue:

```txt
Question asks for first unique element.
```

Mistake:

```txt
Only iterating over map.keySet()
```

Why wrong?

```txt
HashMap does not guarantee original array order.
```

Correct:

```txt
Build map first, then scan original array again.
```

---

### Mistake 4

Find the issue:

```txt
Question only asks if duplicate exists.
```

Mistake:

```txt
Using HashMap unnecessarily.
```

Better:

```txt
Use HashSet.
```

---

## LeetCode Practice

| No. | Problem | Concept |
|---:|---|---|
| 1 | Two Sum | Value-index HashMap |
| 169 | Majority Element | Frequency count |
| 350 | Intersection of Two Arrays II | Frequency + duplicate count |
| 387 | First Unique Character in a String | Frequency + first unique |
| 1365 | How Many Numbers Are Smaller Than Current Number | Count/frequency thinking |
| 1207 | Unique Number of Occurrences | Frequency + HashSet |
| 242 | Valid Anagram | Frequency count |
| 451 | Sort Characters By Frequency | Frequency + sorting |

---

## Answer Key

| Problem | Pattern | Time | Space |
|---:|---|---:|---:|
| 1 | HashMap Frequency | O(n) average | O(n) |
| 2 | HashMap Frequency | O(n) average | O(n) |
| 3 | HashMap Frequency | O(n) average | O(n) |
| 4 | HashMap Frequency | O(n) average | O(n) |
| 5 | HashMap Frequency | O(n) average | O(n) |
| 6 | HashMap Frequency | O(n) average | O(n) |
| 7 | HashMap Lookup | O(n) average | O(n) |
| 8 | HashMap Frequency | O(n + m) average | O(n) |

---

## Before Moving to Pattern 08

You should be able to:

| Skill | Status |
|---|---|
| Explain HashMap | ✅ |
| Use `import java.util.HashMap` | ✅ |
| Use `getOrDefault()` | ✅ |
| Build frequency map | ✅ |
| Count target frequency | ✅ |
| Find most frequent element | ✅ |
| Find first unique element | ✅ |
| Solve Two Sum using HashMap | ✅ |
| Solve intersection with duplicate counts | ✅ |
| Decide HashSet vs HashMap | ✅ |
| Explain O(n) average time | ✅ |
| Explain O(n) space | ✅ |

---

## Next Topic

```txt
Pattern 08: Sorting-Based Patterns
```
