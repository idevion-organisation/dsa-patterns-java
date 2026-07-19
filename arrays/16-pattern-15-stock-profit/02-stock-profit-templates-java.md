# Stock Profit Templates in Java

This file contains common templates for Stock Profit Pattern problems.

Use these templates when the problem asks about buying, selling, and maximizing profit.

---

## Template 1: Maximum Profit With One Transaction

Use when question asks:

```txt
Buy once and sell once.
Return maximum profit.
```

Code:

```java
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
```

---

## Template 2: Maximum Profit With Buy and Sell Days

Use when question asks:

```txt
Return maximum profit with buy day and sell day.
```

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

Return:

```txt
[maxProfit, buyDay, sellDay]
```

---

## Template 3: Maximum Profit With Multiple Transactions

Use when question says:

```txt
You may complete as many transactions as you like.
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

Logic:

```txt
Add every positive price difference.
```

---

## Template 4: Maximum Profit With Transaction Fee

Use when question says:

```txt
Each transaction has a fee.
```

This is a more advanced stock pattern.

Code:

```java
public int maxProfitWithFee(int[] prices, int fee) {
    int hold = -prices[0];
    int cash = 0;

    for (int i = 1; i < prices.length; i++) {
        int previousCash = cash;

        cash = Math.max(cash, hold + prices[i] - fee);
        hold = Math.max(hold, previousCash - prices[i]);
    }

    return cash;
}
```

Meaning:

```txt
cash → maximum profit when not holding stock
hold → maximum profit when holding stock
```

---

## Template 5: Maximum Profit With Cooldown

Use when question says:

```txt
After selling, you cannot buy on the next day.
```

This is an advanced stock DP pattern.

Code:

```java
public int maxProfitWithCooldown(int[] prices) {
    int hold = -prices[0];
    int sold = 0;
    int rest = 0;

    for (int i = 1; i < prices.length; i++) {
        int previousHold = hold;
        int previousSold = sold;
        int previousRest = rest;

        hold = Math.max(previousHold, previousRest - prices[i]);
        sold = previousHold + prices[i];
        rest = Math.max(previousRest, previousSold);
    }

    return Math.max(sold, rest);
}
```

---

## Template 6: Maximum Profit With At Most Two Transactions

Use when question says:

```txt
At most two transactions are allowed.
```

Code:

```java
public int maxProfitTwoTransactions(int[] prices) {
    int buy1 = -prices[0];
    int sell1 = 0;

    int buy2 = -prices[0];
    int sell2 = 0;

    for (int i = 1; i < prices.length; i++) {
        buy1 = Math.max(buy1, -prices[i]);
        sell1 = Math.max(sell1, buy1 + prices[i]);

        buy2 = Math.max(buy2, sell1 - prices[i]);
        sell2 = Math.max(sell2, buy2 + prices[i]);
    }

    return sell2;
}
```

Meaning:

```txt
buy1  → best after first buy
sell1 → best after first sell
buy2  → best after second buy
sell2 → best after second sell
```

---

## Template 7: Kadane Style Stock Profit

Use when you want to connect stock profit with daily differences.

Code:

```java
public int maxProfitKadaneStyle(int[] prices) {
    int currentProfit = 0;
    int maxProfit = 0;

    for (int i = 1; i < prices.length; i++) {
        int diff = prices[i] - prices[i - 1];

        currentProfit = Math.max(0, currentProfit + diff);
        maxProfit = Math.max(maxProfit, currentProfit);
    }

    return maxProfit;
}
```

This is another way to solve one-transaction stock profit.

---

## Template Selection Table

| Requirement | Template |
|---|---|
| Buy once, sell once | One Transaction |
| Return buy/sell days | Profit With Days |
| Many transactions allowed | Multiple Transactions |
| Transaction fee given | Stock With Fee |
| Cooldown after selling | Stock With Cooldown |
| At most two transactions | Two Transactions |
| Kadane connection | Kadane Style Stock |

---

## How to Decide Which Template to Use?

Ask:

```txt
How many transactions are allowed?
```

| Question Says | Use |
|---|---|
| Buy once and sell once | One Transaction |
| As many transactions as you like | Multiple Transactions |
| Transaction fee | DP with fee |
| Cooldown | DP with cooldown |
| At most two transactions | Two transaction DP |
| Return days | Track indexes |

---

## Beginner Rule

For basic stock profit:

```txt
Track minimum price so far.
Try selling on every day.
Update maximum profit.
```

Formula:

```txt
profit = prices[i] - minPrice
```

For multiple transactions:

```txt
Add every positive difference.
```
