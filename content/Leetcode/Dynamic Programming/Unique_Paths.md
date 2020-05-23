+++
title="Unique Paths"
date=2020-05-23
+++

## Problem Link

[https://leetcode.com/problems/unique-paths/](https://leetcode.com/problems/unique-paths/)

## How to solve

## Complexity Analysis

## Time: O(N)

## Space: O(N)

## Solutions

## Python

``` python
    if m == 1 or n == 1:
        return 1

    unique_paths = [[0 for _ in range(m)] for _ in range(2)]

    for i in range(2):
        unique_paths[i][0] = 1

    for j in range(m):
        unique_paths[0][j] = 1

    for i in range(1, n):
        for j in range(1, m):
            unique_paths[i % 2][j] = unique_paths[i % 2 - 1][j] + unique_paths[i % 2][j - 1]

    return unique_paths[-1][-1] if n % 2 == 0 else unique_paths[0][-1]
```

## Go

``` go

```

## Rust

``` rust

```
