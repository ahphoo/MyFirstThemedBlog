+++
title="Climbing Stairs"
date=2020-05-17
+++

## Problem Link

[https://leetcode.com/problems/climbing-stairs/](https://leetcode.com/problems/climbing-stairs/)

## How to solve

## Complexity Analysis

## Time: O(N)

## Space: O(N)

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
