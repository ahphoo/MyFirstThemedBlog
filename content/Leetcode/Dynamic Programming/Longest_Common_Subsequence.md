+++
title="Longest Common Subsequence"
date=2020-05-18
+++

## Problem Link

[https://leetcode.com/problems/longest-increasing-subsequence/](https://leetcode.com/problems/longest-increasing-subsequence/)

## How to solve

## Complexity Analysis

## Time: O(N)

## Space: O(N)

## Solutions

## Python

``` python
rows = len(text1)
cols = len(text2)

dp = [[0 for _ in range(cols + 1)] for _ in range(rows + 1)]

for i in range(1, rows + 1):
    for j in range(1, cols + 1):
        if text1[i - 1] == text2[j - 1]:
            dp[i][j] = dp[i-1][j-1] + 1
        else:
            dp[i][j] = max(dp[i-1][j], dp[i][j-1])

return dp[-1][-1]
```

## Go

``` go

```

## Rust

``` rust

```
