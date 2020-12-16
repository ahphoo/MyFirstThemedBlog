+++
title="Best Time to Buy and Sell Stock"
date=2020-05-09

[taxonomies]
tags = ["Array"]
authors = ["Allan Phu"]
+++

## Problem Link

[https://leetcode.com/problems/best-time-to-buy-and-sell-stock/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

## How to solve

We keep track of two variables, `minBuy` and `maxProfit`. While iterating through the array of stock prices, we keep track of the cheapest/smallest stock price we've seen so far in `minBuy`. We see if we can get a higher profit by selling the stock after we buy it by taking the difference between the current day's stock price and `minBuy` price (i.e. `price - minBuy`). We store the highest profit in `maxProfit`. After iterating through all stock prices in the array, we return `maxProfit`.

## Complexity Analysis

## Time: O(N)

We iterate through the entire array once.

## Space: O(1)

We create two variables that take constant space.

## Solutions

## Python

``` python
def maxProfit(self, prices: List[int]) -> int:
    minBuy = float("inf")
    maxProfit = 0

    for price in prices:
        minBuy = min(minBuy, price)
        maxProfit = max(maxProfit, price - minBuy)

    return maxProfit
```

## Go

``` go
func maxProfit(prices []int) int {
    var minBuy int = math.MaxInt32
    var maxProfit int = 0

    for _, price := range prices {
        minBuy = Min(minBuy, price)
        maxProfit = Max(maxProfit, price - minBuy)
    }

    return maxProfit
}

func Min(x, y int) int {
    if x < y {
        return x
    }
    return y
}

func Max(x, y int) int {
    if x > y {
        return x
    }
    return y
}
```

## Rust

``` rust
pub fn max_profit(prices: Vec<i32>) -> i32 {
    let mut minBuy = std::i32::MAX;
    let mut maxProfit = 0;

    for &price in &prices {
        minBuy = std::cmp::min(minBuy, price);
        maxProfit = std::cmp::max(maxProfit, price - minBuy);
    }

    maxProfit
}
```

## Java

```java
public int maxProfit(int[] prices) {
    int profit = 0;
    int minBuy = Integer.MAX_VALUE;
        
    for (int price : prices) {
        minBuy = Math.min(minBuy, price);
        profit = Math.max(profit, price - minBuy);
    }
        
    return profit;
}
```
