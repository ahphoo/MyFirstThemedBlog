+++
title="Maximum Subarray"
date=2020-05-10
+++

## Problem Link

[https://leetcode.com/problems/maximum-subarray/](https://leetcode.com/problems/maximum-subarray/)

## How to solve

## Complexity Analysis

## Time: O(N)

## Space: O(1)

## Solutions

## Python

``` python
cur_sum = nums[0]
max_sum = nums[0]

for i in range(1, len(nums)):
    cur_sum = max(cur_sum + nums[i], nums[i])
    max_sum = max(max_sum, cur_sum)

return max_sum
```

## Go

``` go
```

## Rust

``` rust
```
