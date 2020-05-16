+++
title="Counting Bits"
date=2020-05-14
+++

## Problem Link

[https://leetcode.com/problems/counting-bits/](https://leetcode.com/problems/counting-bits/)

## How to solve

## Complexity Analysis

## Time: O(n)

## Space: O(n)

## Solutions

## Python

``` python
def countBits(self, num: int) -> List[int]:
    count = [0 for _ in range(num + 1)]

    for i in range(1, num + 1):
        count[i] = count[i & (i - 1)] + 1

    return count
```

## Go

``` go

```

## Rust

``` rust

```
