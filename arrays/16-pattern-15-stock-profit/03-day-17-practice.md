# Day 17 Practice: Pattern 15 Stock Profit

Today's goal is to master the **Stock Profit Pattern**.

This pattern is used when array values represent prices over days and we need to maximize profit.

---

## Practice Method

For every problem, write:

```txt
Given:
Asked:
One transaction or multiple transactions?
Need profit only or days also?
Can I buy before sell?
Pattern:
Return:
Time Complexity:
Space Complexity:
```

Example:

```txt
Problem: Best Time to Buy and Sell Stock

Given: prices array
Asked: maximum profit
One transaction or multiple transactions? one transaction
Need profit only or days also? profit only
Can I buy before sell? yes
Pattern: Stock Profit
Return: maximum profit
Time: O(n)
Space: O(1)
```

---

## Manual Practice Problems

### 1. One Transaction Profit

```txt
Input:
prices = [7, 1, 5, 3, 6, 4]

Output:
5
```

Why?

```txt
Buy at 1
Sell at 6
Profit = 5
```

---

### 2. No Profit Possible

```txt
Input:
prices = [7, 6, 4, 3, 1]

Output:
0
```

Think:

```txt
Price keeps decreasing.
No profitable transaction is possible.
```

---

### 3. Increasing Prices

```txt
Input:
prices = [1, 2, 3, 4, 5]

Output:
4
```

Why?

```txt
Buy at 1
Sell at 5
```

---

### 4. Return Buy and Sell Days

```txt
Input:
prices = [7, 1, 5, 3, 6, 4]

Output:
profit = 5
buyDay = 1
sellDay = 4
```

Think:

```txt
Track minIndex along with minPrice.
```

---

### 5. Multiple Transactions

```txt
Input:
prices = [7, 1, 5, 3, 6, 4]

Output:
7
```

Why?

```txt
Buy at 1, sell at 5 → profit 4
Buy at 3, sell at 6 → profit 3
Total = 7
```

---

### 6. Multiple Transactions Increasing Prices

```txt
Input:
prices = [1, 2, 3, 4, 5]

Output:
4
```

Think:

```txt
Add every positive difference.
```

---

### 7. Single Day Price

```txt
Input:
prices = [5]

Output:
0
```

Think:

```txt
Cannot sell after buying.
```

---

### 8. Kadane Style Stock Profit

```txt
Input:
prices = [7, 1, 5, 3, 6, 4]

Differences:
[-6, 4, -2, 3, -2]

Output:
5
```

Think:

```txt
Maximum subarray sum of daily differences.
```

---

## Dry Run Practice

Dry run:

```txt
prices = [7, 1, 5, 3, 6, 4]
```

Fill this table:

| Day | Price | minPrice | Profit if sold today | maxProfit |
|---:|---:|---:|---:|---:|
| 0 | 7 | 7 | - | 0 |
| 1 |  |  |  |  |
| 2 |  |  |  |  |
| 3 |  |  |  |  |
| 4 |  |  |  |  |
| 5 |  |  |  |  |

---

## Completed Dry Run Answer

```txt
prices = [7, 1, 5, 3, 6, 4]
```

Initial:

```txt
minPrice = 7
maxProfit = 0
```

| Day | Price | minPrice | Profit if sold today | maxProfit |
|---:|---:|---:|---:|---:|
| 0 | 7 | 7 | - | 0 |
| 1 | 1 | 1 | - | 0 |
| 2 | 5 | 1 | 4 | 4 |
| 3 | 3 | 1 | 2 | 4 |
| 4 | 6 | 1 | 5 | 5 |
| 5 | 4 | 1 | 3 | 5 |

Answer:

```txt
5
```

---

## Multiple Transactions Dry Run

```txt
prices = [7, 1, 5, 3, 6, 4]
```

| i | prices[i - 1] | prices[i] | Difference | Add? | Total Profit |
|---:|---:|---:|---:|---|---:|
| 1 | 7 | 1 | -6 | No | 0 |
| 2 | 1 | 5 | 4 | Yes | 4 |
| 3 | 5 | 3 | -2 | No | 4 |
| 4 | 3 | 6 | 3 | Yes | 7 |
| 5 | 6 | 4 | -2 | No | 7 |

Answer:

```txt
7
```

---

## Common Mistake Practice

### Mistake 1

Find the issue:

```txt
Sorting prices before solving.
```

Problem:

```txt
Sorting destroys day order.
Buy must happen before sell.
```

Correct:

```txt
Scan prices from left to right.
```

---

### Mistake 2

Find the issue:

```java
int maxProfit = Integer.MIN_VALUE;
```

Problem:

```txt
If no profit is possible, answer should be 0.
```

Correct:

```java
int maxProfit = 0;
```

---

### Mistake 3

Find the issue:

```txt
Question allows multiple transactions.
```

Mistake:

```txt
Using one-transaction minPrice method only.
```

Correct:

```txt
Add every positive difference.
```

---

### Mistake 4

Find the issue:

```txt
Question allows only one transaction.
```

Mistake:

```txt
Adding every positive difference.
```

Correct:

```txt
Track minPrice and maxProfit.
```

---

### Mistake 5

Find the issue:

```txt
Trying to sell before buying.
```

Problem:

```txt
Not allowed.
```

Correct:

```txt
Buy day must be before sell day.
```

---

## LeetCode Practice

| No. | Problem | Concept |
|---:|---|---|
| 121 | Best Time to Buy and Sell Stock | One transaction |
| 122 | Best Time to Buy and Sell Stock II | Multiple transactions |
| 714 | Best Time to Buy and Sell Stock with Transaction Fee | Stock DP |
| 309 | Best Time to Buy and Sell Stock with Cooldown | Stock DP |
| 123 | Best Time to Buy and Sell Stock III | At most two transactions |
| 188 | Best Time to Buy and Sell Stock IV | At most k transactions |
| 53 | Maximum Subarray | Kadane connection |

---

## Answer Key

| Problem | Pattern | Time | Space |
|---:|---|---:|---:|
| 1 | Stock Profit One Transaction | O(n) | O(1) |
| 2 | Stock Profit One Transaction | O(n) | O(1) |
| 3 | Stock Profit One Transaction | O(n) | O(1) |
| 4 | Stock Profit With Days | O(n) | O(1) |
| 5 | Stock Profit Multiple Transactions | O(n) | O(1) |
| 6 | Stock Profit Multiple Transactions | O(n) | O(1) |
| 7 | Stock Profit Edge Case | O(1) | O(1) |
| 8 | Kadane Style Stock Profit | O(n) | O(1) |

---

## Before Moving to Pattern 16

You should be able to:

| Skill | Status |
|---|---|
| Explain Stock Profit Pattern | ✅ |
| Identify stock price array problems | ✅ |
| Track minimum price so far | ✅ |
| Calculate profit if selling today | ✅ |
| Solve one-transaction profit | ✅ |
| Return buy and sell days | ✅ |
| Solve multiple transaction profit | ✅ |
| Avoid sorting prices | ✅ |
| Explain relation with Kadane's Algorithm | ✅ |
| Explain O(n) time and O(1) space | ✅ |
| Know one transaction vs multiple transactions | ✅ |

---

## Next Topic

```txt
Pattern 16: XOR and Math Formula
```
