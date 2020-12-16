+++
title="House Robber"
date=2020-05-19

[taxonomies]
tags = ["Dynamic Programming"]
authors = ["Allan Phu"]
+++

## Problem Link

[https://leetcode.com/problems/house-robber/](https://leetcode.com/problems/house-robber/)

## How to solve

### Table

| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |

Every house, we decide if it is more profitable to rob the house or skip it.

## Complexity Analysis

## Time: O(N)

For every house, we decide whether to rob it or skip it.

## Space: O(N)

We store the maximum amount of money we can rob at house every.

## Solutions

## Python

``` python
def rob(self, nums: List[int]) -> int:
    if not nums:
        return 0
    if len(nums) <= 2:
        return max(nums)

    dp = [0 for _ in range(len(nums))]
    dp[0] = nums[0]
    dp[1] = max(nums[0], nums[1])

    for i in range(2, len(nums)):
        dp[i] = max(dp[i - 1], nums[i] + dp[i - 2])

    return dp[-1]
```

## Go

``` go
func rob(nums []int) int {
    if len(nums) == 0 {
        return 0
    } else if len(nums) == 1 {
        return nums[0]
    } else if len(nums) == 2 {
        return max(nums[0], nums[1])
    }

    dp := make([]int, len(nums))
    dp[0] = nums[0]
    dp[1] = max(nums[0], nums[1])
    for i := 2; i < len(nums); i++ {
        dp[i] = max(dp[i - 1], nums[i] + dp[i - 2])
    }
    return dp[len(nums) - 1]
}

func max(x int, y int) int {
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
    pub fn rob(nums: Vec<i32>) -> i32 {
        if nums.len() == 0 {
            return 0;
        } else if nums.len() == 1 {
            return nums[0];
        } else if nums.len() == 2 {
            return max(nums[0], nums[1]);
        }

        let mut dp = vec![0; nums.len()];
        dp[0] = nums[0];
        dp[1] = max(nums[0], nums[1]);

        for i in 2..nums.len() {
            dp[i] = max(dp[i - 1], nums[i] + dp[i - 2])
        }

        dp[nums.len() - 1]
    }
}
```
