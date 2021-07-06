+++
title="Single Number"
date=2020-04-01
+++

## Problem Link

[https://leetcode.com/problems/single-number/](https://leetcode.com/problems/single-number/)

## How to solve

## Complexity Analysis

## Time: O(N)

## Space: O(1)

## Solutions

## Python

``` python
def singleNumber(self, nums: List[int]) -> int:
    singleNum = 0
    for num in nums:
        singleNum ^= num
    return singleNum
```

## Go

## Rust
