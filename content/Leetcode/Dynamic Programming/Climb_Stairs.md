+++
title="Climbing Stairs"
date=2020-05-17
+++

## Problem Link

[https://leetcode.com/problems/climbing-stairs/](https://leetcode.com/problems/climbing-stairs/)

## How to solve

There is only one way to climb 1 stair (single step).

There are two ways to climb 2 stairs,

1. single step + single step
2. double step

Note that we can climb 3 stairs either by taking a single step after climbing 2 stairs, or a double step after climbing 1 stair. That is,

Ways to climb 3 stairs = Ways to climb 2 stairs + Ways to climb 1 stair

The same equation holds for finding the number of ways to climb N stairs.

Ways to climb N stairs = Ways to climb N - 2 stairs + Ways to climb N - 1 stairs.

## Complexity Analysis

## Time: O(N)

We calculate the ways we can climb 1, 2, ..., N stairs.

## Space: O(N)

We allocate an array of size N to hold the number of ways we can climb 1, 2, ..., N stairs.

## Solutions

## Python

``` python
def climbStairs(self, n: int) -> int:
    if n <= 2:
        return n

    dp = [0 for _ in range(n + 1)]

    dp[1] = 1
    dp[2] = 2

    for i in range(3, len(dp)):
        dp[i] = dp[i - 2] + dp[i - 1]

    return dp[-1]
```

## Go

``` go
func climbStairs(n int) int {
    if n <= 2 {
        return n
    }

    dp := make([]int, n + 1)

    dp[1] = 1
    dp[2] = 2

    for i := 3; i < n + 1; i++ {
        dp[i] = dp[i - 2] + dp[i - 1]
    }

    return dp[n]
}
```

## Rust

``` rust
pub fn climb_stairs(n: i32) -> i32 {
    if n <= 2 {
        return n;
    }

    let mut dp = vec![0; (n + 1) as usize];

    dp[1] = 1;
    dp[2] = 2;

    for i in 3..n + 1 {
        dp[i as usize] = dp[(i - 2) as usize] + dp[(i - 1) as usize];
    }

    dp[n as usize]
}
```
