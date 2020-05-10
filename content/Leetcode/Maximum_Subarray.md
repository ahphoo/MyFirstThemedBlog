+++
title="Maximum Subarray"
date=2020-05-10
+++

## Problem Link

[https://leetcode.com/problems/maximum-subarray/](https://leetcode.com/problems/maximum-subarray/)

## How to solve

We want to find the contiguous subarray with the largest sum. First, we create two variables to keep track of the current sum and the maximum sum, initializing both of them to `nums[0]`. We iterate through the nums array starting at index 1. For each number `num` in the nums array, we decide whether to include `num` in our current subarray sum or to reset the current subarray sum to be `num`. That is, we take the max of `num` plus the current sum, or `num`. Next, we update the maximum sum, taking the max of maximum sum and current sum. After iterating through all numbers in the nums array, we return the maximum sum.

## Complexity Analysis

## Time: O(N)

We iterate through **N - 1** elements, calculating the current sum and maximum sum at each step.

## Space: O(1)

We have two variables that keep track of the current sum and the maximum sum at each step.

## Solutions

## Python

``` python
def maxSubArray(self, nums: List[int]) -> int:
    cur_sum = nums[0]
    max_sum = nums[0]

    for i in range(1, len(nums)):
        cur_sum = max(cur_sum + nums[i], nums[i])
        max_sum = max(max_sum, cur_sum)

    return max_sum
```

## Go

``` go
func maxSubArray(nums []int) int {
    cur_sum := nums[0]
    max_sum := nums[0]

    for i := 1; i < len(nums); i++ {
        cur_sum = Max(cur_sum + nums[i], nums[i])
        max_sum = Max(max_sum, cur_sum)
    }

    return max_sum
}

func Max(x, y int) int {
    if x > y {
        return x
    }
    return y
}
```

## Rust

``` rust
use std::cmp::max;

impl Solution {
    pub fn max_sub_array(nums: Vec<i32>) -> i32 {
        let mut cur_sum: i32 = nums[0];
        let mut max_sum: i32 = nums[0];

        for i in 1..nums.len() {
            cur_sum = max(cur_sum + nums[i], nums[i]);
            max_sum = max(max_sum, cur_sum);
        }

        max_sum
    }
}
```
