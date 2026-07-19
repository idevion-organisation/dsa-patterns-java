# Pattern 15: Stock Profit Pattern

Stock Profit Pattern is an array pattern used when we need to find the best profit from buying and selling stock.

It is commonly used in problems where each array element represents the stock price on a particular day.

---

## What Is Stock Profit Pattern?

Suppose we have:

```txt
prices = [7, 1, 5, 3, 6, 4]
```

Each value represents stock price on that day.

```txt
Day 0 → price 7
Day 1 → price 1
Day 2 → price 5
Day 3 → price 3
Day 4 → price 6
Day 5 → price 4
```

We need to buy at a low price and sell at a higher price later.

Best choice:

```txt
Buy at 1
Sell at 6
Profit = 6 - 1 = 5
```

Answer:

```txt
5
```

---

## Important Rule

You must buy before you sell.

This is valid:

```txt
Buy on Day 1
Sell on Day 4
```

This is not valid:

```txt
Sell first
Buy later
```

So we always move from left to right.

---

## Simple Meaning

```txt
Track the minimum price so far
Calculate profit if selling today
Keep the maximum profit
```

---

## Pattern Signal

Think of Stock Profit Pattern when the question says:

```txt
stock price
buy and sell
maximum profit
minimum buying price
sell after buying
one transaction
multiple transactions
best time to buy
best time to sell
```

Most common signal:

```txt
Best Time to Buy and Sell Stock
```

---

## Main Idea

For every day:

```txt
If today's price is lower than previous minimum price,
update minimum price.

Otherwise,
calculate profit if we sell today.
```

Formula:

```txt
profit = current price - minimum price so far
```

Then update:

```txt
maxProfit = maximum of current maxProfit and profit
```

---

## Why This Works?

To get maximum profit:

```txt
buy price should be minimum
sell price should be maximum after buying
```

While scanning from left to right:

```txt
minimum price so far = best possible buying price before current day
current price = possible selling price today
```

So every day, we check:

```txt
What if I sell today?
```

---

## Brute Force Approach

A beginner may check every pair of days.

```java
public int maxProfit(int[] prices) {
    int maxProfit = 0;

    for (int buy = 0; buy < prices.length; buy++) {
        for (int sell = buy + 1; sell < prices.length; sell++) {
            int profit = prices[sell] - prices[buy];

            if (profit > maxProfit) {
                maxProfit = profit;
            }
        }
    }

    return maxProfit;
}
```

Time Complexity:

```txt
O(n²)
```

This works, but it is slow for large arrays.

---

## Optimized Approach

Instead of checking every pair, keep track of:

```txt
minimum price so far
maximum profit so far
```

This reduces time to:

```txt
O(n)
```

---

## Complete Java Code: One Transaction

Problem:

```txt
Find maximum profit if you can buy once and sell once.
```

Code:

```java
class Solution {
    public int maxProfit(int[] prices) {
        int minPrice = prices[0];
        int maxProfit = 0;

        for (int i = 1; i < prices.length; i++) {
            if (prices[i] < minPrice) {
                minPrice = prices[i];
            }
            else {
                int profit = prices[i] - minPrice;

                if (profit > maxProfit) {
                    maxProfit = profit;
                }
            }
        }

        return maxProfit;
    }
}
```

---

## Line-by-Line Explanation

```java
int minPrice = prices[0];
```

Assume the first price is the minimum buying price.

---

```java
int maxProfit = 0;
```

Maximum profit starts from `0`.

If no profit is possible, answer remains `0`.

---

```java
for (int i = 1; i < prices.length; i++)
```

Start checking from the second day.

---

```java
if (prices[i] < minPrice)
```

If today's price is lower than previous minimum price, update buying price.

---

```java
minPrice = prices[i];
```

This becomes the best buying price so far.

---

```java
int profit = prices[i] - minPrice;
```

Calculate profit if we sell today.

---

```java
maxProfit = Math.max(maxProfit, profit);
```

Update best profit.

---

```java
return maxProfit;
```

Return maximum possible profit.

---

## Dry Run

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

Best transaction:

```txt
Buy at 1
Sell at 6
```

---

## Case 1: Profit Possible

Input:

```txt
prices = [7, 1, 5, 3, 6, 4]
```

Output:

```txt
5
```

Reason:

```txt
Buy at 1
Sell at 6
Profit = 5
```

---

## Case 2: No Profit Possible

Input:

```txt
prices = [7, 6, 4, 3, 1]
```

Output:

```txt
0
```

Reason:

```txt
Price keeps decreasing.
No profitable sell is possible.
```

So we return:

```txt
0
```

---

## Case 3: Increasing Prices

Input:

```txt
prices = [1, 2, 3, 4, 5]
```

Output:

```txt
4
```

Reason:

```txt
Buy at 1
Sell at 5
Profit = 4
```

---

## Variation 1: Return Buy and Sell Days

Sometimes we may need to return the buy day and sell day.

Code:

```java
public int[] maxProfitDays(int[] prices) {
    int minPrice = prices[0];
    int minIndex = 0;

    int maxProfit = 0;
    int buyDay = 0;
    int sellDay = 0;

    for (int i = 1; i < prices.length; i++) {
        if (prices[i] < minPrice) {
            minPrice = prices[i];
            minIndex = i;
        }
        else {
            int profit = prices[i] - minPrice;

            if (profit > maxProfit) {
                maxProfit = profit;
                buyDay = minIndex;
                sellDay = i;
            }
        }
    }

    return new int[]{maxProfit, buyDay, sellDay};
}
```

Return format:

```txt
[maxProfit, buyDay, sellDay]
```

---

## Variation 2: Multiple Transactions

Sometimes the question says:

```txt
You may complete as many transactions as you like.
```

This means:

```txt
Buy and sell multiple times
But you must sell before buying again
```

Example:

```txt
prices = [7, 1, 5, 3, 6, 4]
```

Transactions:

```txt
Buy at 1, sell at 5 → profit 4
Buy at 3, sell at 6 → profit 3
```

Total profit:

```txt
7
```

---

## Logic for Multiple Transactions

If tomorrow's price is higher than today's price, take the profit.

```txt
profit += prices[i] - prices[i - 1]
```

Only when:

```txt
prices[i] > prices[i - 1]
```

Code:

```java
public int maxProfitMultipleTransactions(int[] prices) {
    int profit = 0;

    for (int i = 1; i < prices.length; i++) {
        if (prices[i] > prices[i - 1]) {
            profit += prices[i] - prices[i - 1];
        }
    }

    return profit;
}
```

---

## Dry Run: Multiple Transactions

```txt
prices = [7, 1, 5, 3, 6, 4]
```

| i | prices[i - 1] | prices[i] | Difference | Take Profit? | Total |
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

## One Transaction vs Multiple Transactions

| Point | One Transaction | Multiple Transactions |
|---|---|---|
| Buy count | Once | Many times |
| Sell count | Once | Many times |
| Main variable | `minPrice` | `profit` |
| Logic | Track minimum price | Add every positive difference |
| Example problem | Best Time to Buy and Sell Stock I | Best Time to Buy and Sell Stock II |

---

## Stock Profit vs Kadane's Algorithm

Stock Profit Pattern is related to Kadane's Algorithm.

For one transaction:

```txt
profit = sell price - buy price
```

We are basically finding the maximum difference where selling day comes after buying day.

Kadane's Algorithm finds:

```txt
maximum subarray sum
```

Stock problem can also be converted into daily differences.

Example:

```txt
prices = [7, 1, 5, 3, 6, 4]
```

Differences:

```txt
[-6, 4, -2, 3, -2]
```

Maximum subarray sum of differences:

```txt
4 + (-2) + 3 = 5
```

Answer:

```txt
5
```

But beginner-friendly method is:

```txt
Track minPrice and maxProfit
```

---

## Time and Space Complexity

For one transaction:

| Complexity | Value |
|---|---:|
| Time Complexity | O(n) |
| Space Complexity | O(1) |

For multiple transactions:

| Complexity | Value |
|---|---:|
| Time Complexity | O(n) |
| Space Complexity | O(1) |

---

## Common Mistakes

### 1. Selling Before Buying

Wrong thinking:

```txt
Buy at 1 after selling at 7
```

You must buy first and sell later.

Always scan from left to right.

---

### 2. Initializing `maxProfit` Incorrectly

For stock profit, no profit means answer should be:

```txt
0
```

So:

```java
int maxProfit = 0;
```

is correct.

Do not return negative profit.

---

### 3. Updating Profit Before Minimum Price

If current price is lower, update `minPrice`.

Then use future prices for profit.

---

### 4. Confusing One Transaction and Multiple Transactions

If question says:

```txt
buy once and sell once
```

Use:

```txt
minPrice + maxProfit
```

If question says:

```txt
as many transactions as you like
```

Use:

```txt
add every positive difference
```

---

### 5. Sorting the Prices

Do not sort stock prices.

Why?

```txt
Days matter.
Buying must happen before selling.
```

Sorting destroys the original day order.

---

## Beginner Checklist

Before applying Stock Profit Pattern, ask:

```txt
1. Does the array represent prices by day?
2. Do I need maximum profit?
3. Is only one transaction allowed?
4. Are multiple transactions allowed?
5. Must I buy before selling?
6. Should I return profit only or buy/sell days also?
7. Can profit be negative?
8. Should I avoid sorting?
9. What is my current minimum price?
10. What is my maximum profit so far?
```

---

## Pattern Summary

| Point | Meaning |
|---|---|
| Pattern Name | Stock Profit Pattern |
| Pattern Number | 15 |
| Used For | Buy/sell stock profit problems |
| Main Variables | `minPrice`, `maxProfit` |
| One Transaction Logic | Track minimum price so far |
| Multiple Transactions Logic | Add positive differences |
| Time | O(n) |
| Space | O(1) |
| Important Rule | Buy before sell |
| Avoid | Sorting prices |

---

## Next Pattern

```txt
Pattern 16: XOR and Math Formula
```
