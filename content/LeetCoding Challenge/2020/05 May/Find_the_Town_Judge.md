+++
title="Find the Town Judge"
date=2020-05-10
+++

## Problem Link

[https://leetcode.com/problems/find-the-town-judge/](https://leetcode.com/problems/find-the-town-judge/)

## How to solve

## Complexity Analysis

## Time: O(N)

## Space: O(N)

## Solutions

## Python

``` python
num_of_trusts = [0 for _ in range(N + 1)]

for t in trust:
    num_of_trusts[t[1]] += 1
    num_of_trusts[t[0]] -= 1

for i in range(1, N + 1):
    if num_of_trusts[i] == N - 1:
        return i
return -1
```

## Go

## Rust
