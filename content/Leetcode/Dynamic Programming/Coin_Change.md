+++
title="Coin Change"
date=2020-05-17

[taxonomies]
tags = ["Dynamic Programming"]
authors = ["Allan Phu"]
+++

## Problem Link

[https://leetcode.com/problems/coin-change/](https://leetcode.com/problems/coin-change/)

## How to solve

We create an array `num_coins` to hold the number of coins needed to obtain `0`, `1`, ..., `amount`. We also create an array `last_coin_used` of the same size, which holds the last coin demonimation used to obtain each amount of change.

Since it is impossible to make `0` change from positive valued coins, we set `num_coins[0] = 0`.

For every coin in the coins array, we see if we can obtain each amount of change (i.e. `coin`, `coin + 1`, ..., `amount`), using less coins. Suppose our current coin is of demonimation `c`. We check if we can use less coins by adding 1 to the minimum number of coins needed to make `change - c`. More specifically,

`num_coins[change] = min(num_coins[change], num_coins[change - c] + 1)`

We return the last element in `num_coins`, which is the minimum number of coins needed to make change `amount`.

## Complexity Analysis

## Time: O(amount * len(coins))

For every demonimation of coin, we check if we can obtain amounts `coin`, `coin + 1`, ..., `amount` using less coins.

## Space: O(amount)

We create an array to hold the number of coins needed to obtain `0`, `1`, ..., `amount`. We also create an array to remember the last coin used to obtain each amount.

## Solutions

## Python

``` python
    def coinChange(self, coins: List[int], amount: int) -> int:
        num_coins = [float("inf") for _ in range(amount + 1)]
        last_coin_used = [None for _ in range(amount + 1)]
        num_coins[0] = 0

        for coin in coins:
            for change in range(coin, amount + 1):
                if num_coins[change - coin] + 1 < num_coins[change]:
                    last_coin_used[change] = coin
                num_coins[change] = min(num_coins[change], num_coins[change - coin] + 1)

        # Print coins used to make amount
        ptr = amount
        while last_coin_used[ptr]:
            print(last_coin_used[ptr], end = " ")
            ptr -= last_coin_used[ptr]

        return num_coins[-1] if num_coins[-1] != float("inf") else -1
```

## Go

``` go
func coinChange(coins []int, amount int) int {
    num_coins := make([]int, amount + 1)
    last_coin_used := make([]int, amount + 1)

    for i := range num_coins {
        num_coins[i] = amount + 1
    }

    for i := range last_coin_used {
        last_coin_used[i] = -1
    }

    num_coins[0] = 0

    for _, coin := range(coins) {
        for change := coin; change < amount + 1; change++ {
            if num_coins[change - coin] + 1 < num_coins[change] {
                last_coin_used[change] = coin
                num_coins[change] = num_coins[change - coin] + 1
            }
        }
    }

    ptr := amount
    for last_coin_used[ptr] != -1 {
        fmt.Print(last_coin_used[ptr], " ")
        ptr -= last_coin_used[ptr]
    }

    if num_coins[len(num_coins) - 1] != amount + 1 {
        return num_coins[amount]
    }
    return -1
}
```

## Rust

``` rust
pub fn coin_change(coins: Vec<i32>, amount: i32) -> i32 {
    let amount = amount as usize;
    let mut num_coins = vec![amount + 1; amount + 1];
    let mut last_coin_used = vec![std::i32::MIN; amount + 1];
    num_coins[0] = 0;

    for &coin in &coins {
        let coin = coin as usize;
        for change in coin..amount + 1 {
            if num_coins[change - coin] + 1 < num_coins[change] {
                last_coin_used[change] = coin as i32;
                num_coins[change] = num_coins[change - coin] + 1;
            }
        }
    }

    let mut ptr = amount;
    while last_coin_used[ptr] != std::i32::MIN {
        println!("{} ", last_coin_used[ptr]);
        ptr -= last_coin_used[ptr] as usize;
    }

    if num_coins[amount] != amount + 1 {
        return num_coins[amount] as i32;
    }
    -1
}
```
