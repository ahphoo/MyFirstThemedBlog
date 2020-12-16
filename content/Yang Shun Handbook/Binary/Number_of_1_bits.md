+++
title="Number of 1 bits"
date=2020-05-14

[taxonomies]
tags = ["Binary"]
authors = ["Allan Phu"]
+++

## Problem Link

[https://leetcode.com/problems/number-of-1-bits/](https://leetcode.com/problems/number-of-1-bits/)

## How to solve

We want to count the number of 1 bits in a number. Note that for a number `n`, we can calculate `n-1` by turning off the rightmost one bit and flipping all zero bits to the right of the rightmost one bit. If we perform the bitwise operation `n & (n-1)`, all the bits to the left of the rightmost one will be preserved, while all bits to the left and including the rightmost one will be set to zero. We keep a count of how many times we can repeat this process until `n` becomes 0.

## Complexity Analysis

## Time: O(log(n)) (or O(1) if using 32-bit integer)

In the worst case, the binary string representation of `n` has all ones. Since `n` can be represented using at most floor(log(n)) + 1 bits, we turn off at most log(n) ones.

## Space: O(1)

We use a temp variable to keep track of the number of ones we turn off in `n`.

## Solutions

## Python

``` python
def hammingWeight(self, n: int) -> int:
    total = 0

    while n:
        total += 1
        n &= (n - 1)

    return total
```

## Go

``` go
func hammingWeight(num uint32) int {
    total := 0

    for num != 0 {
        total += 1
        num &= (num - 1)
    }

    return total
}
```

## Rust

``` rust
pub fn hammingWeight (n: u32) -> i32 {
    let mut num = n;
    let mut total = 0;

    while num != 0 {
        total += 1;
        num &= (num - 1);
    }

    total
}
```
