+++
title="Reverse Bits"
date=2020-05-14
+++

## Problem Link

[https://leetcode.com/problems/reverse-bits/](https://leetcode.com/problems/reverse-bits/)

## How to solve

## Complexity Analysis

## Time: O(N log N)

## Space: O(1)

## Solutions

## Python

``` python
def reverseBits(self, n: int) -> int:
    n = (n & 0xFFFF0000) >> 16 | (n & 0x0000FFFF) << 16
    n = (n & 0xFF00FF00) >> 8  | (n & 0x00FF00FF) << 8
    n = (n & 0xF0F0F0F0) >> 4  | (n & 0x0F0F0F0F) << 4
    n = (n & 0xCCCCCCCC) >> 2  | (n & 0x33333333) << 2
    n = (n & 0xAAAAAAAA) >> 1  | (n & 0x55555555) << 1
    return n
```

## Go

``` go

```

## Rust

``` rust

```
