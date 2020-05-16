+++
title="Reverse Bits"
date=2020-05-14
+++

## Problem Link

[https://leetcode.com/problems/reverse-bits/](https://leetcode.com/problems/reverse-bits/)

## How to solve

We can solve this problem using Divide-and-Conquer. Given a 32-bit integer, we can break up the problem into several subproblems. Our subproblem is to reverse half of the bits. To do this, we can take the first 16 bits and swap them with the last 16 bits. Note that not all bits within each group of 16 bits are sorted relative to each other. Within each group of 16 bits, we swap the first 8 bits with the last 8 bits. We repeat this partitioning until we get our reversed number.

## Complexity Analysis

## Time: O(N log N)

Second case of Master's Theorem. We mask off 2 * `N/2` bits. Then we combine `N` bits. We repeat on a subproblem of size `N/2`.

## Space: O(1)

We save the results of our bit operations into `n`.

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
func reverseBits(num uint32) uint32 {
    num = num >> 16 | num << 16
    num = (num & 0xFF00FF00) >> 8  | (num & 0x00FF00FF) << 8
    num = (num & 0xF0F0F0F0) >> 4  | (num & 0x0F0F0F0F) << 4
    num = (num & 0xCCCCCCCC) >> 2  | (num & 0x33333333) << 2
    num = (num & 0xAAAAAAAA) >> 1  | (num & 0x55555555) << 1
    return num
}
```

## Rust

``` rust

```
