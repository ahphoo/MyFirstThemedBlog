+++
title="Maximum Product Subarray"
date=2020-05-11
+++

## Problem Link

[https://leetcode.com/problems/maximum-product-subarray/](https://leetcode.com/problems/maximum-product-subarray/)

## How to solve

We want to find the contiguous subarray with the largest product. First, we create two variables to keep track of the local minimum product and the local maximum product, initializing both of them to `nums[0]`. We iterate through the nums array starting at index 1. For each number `num` in the nums array, we decide whether to include `num` in our current subarray product or to reset the current subarray product to be `num`. That is, we take the max of `num` times local max, `num` times local min, or `num`. Next, we update the global maximum product, taking the max of the global maximum product and local maximum product. After iterating through all numbers in the nums array, we return the global maximum product.

## Complexity Analysis

## Time: O(N)

We iterate through **N - 1** elements, updating the local minimum product, local maximum product, and global maximum product at each step.

## Space: O(1)

We just have variables that keep track of the current product and the maximum product at each step.

## Solutions

## Python

``` python
def maxProduct(self, nums: List[int]) -> int:
    if not nums:
        return 0
    local_min = nums[0]
    local_max = nums[0]
    global_max = nums[0]

    for i in range(1, len(nums)):
        cur_min = min(nums[i], local_min * nums[i], local_max * nums[i])
        cur_max = max(nums[i], local_min * nums[i], local_max * nums[i])
        global_max = max(global_max, local_max)

        local_min = cur_min
        local_max = cur_max

    return global_max
```

## Go

``` go
func maxProduct(nums []int) int {
    local_min := nums[0]
    local_max := nums[0]
    global_max := nums[0]

    for i := 1; i < len(nums); i++ {
        cur_min := min(nums[i], local_min * nums[i], local_max * nums[i])
        cur_max := max(nums[i], local_min * nums[i], local_max * nums[i])
        global_max = max(max_sum, cur_max)

        local_min = cur_min
        local_max = cur_max
    }

    return global_max
}

func max(x, y int) int {
    if x > y {
        return x
    }
    return y
}

func min(x, y int) int {
    if x > y {
        return x
    }
    return y
}
```

## Rust

``` rust
use std::cmp::{min, max};

impl Solution {
    pub fn max_product(nums: Vec<i32>) -> i32 {
        let mut local_min: i32 = nums[0];
        let mut local_max: i32 = nums[0];
        let mut global_max: i32 = nums[0];
        let mut cur_min: i32 = nums[0];
        let mut cur_max: i32 = nums[0];

        for i in 1..nums.len() {
            cur_min = min(nums[i], min(local_min * nums[i], local_max * nums[i]));
            cur_max = max(nums[i], max(local_min * nums[i], local_max * nums[i]));
            global_max = max(global_max, cur_max);
            local_min = cur_min;
            local_max = cur_max;
        }

        global_max
    }
}
```
