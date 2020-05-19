+++
title="Combination Sum IV"
date=2020-05-19
+++

## Problem Link

[https://leetcode.com/problems/combination-sum-iv](https://leetcode.com/problems/combination-sum-iv)

## How to solve

Create a dp array of size target + 1. dp[i] represents the number of combinations of numbers in `nums` that add up to `i`. 

For every `i`, iterate through `nums` and add to dp[i] the number of combinations that add up to i - num (i.e. dp[i - num]).

## Complexity Analysis

## Time: O(target * len(nums))

We calculate the possible number of combinations for 0, 1, ..., target. For every number `i`, we iterate through every number in `nums` and see if we can add the number of combinations that add up to `i = num`.

## Space: O(target)

The dp array is of size target + 1.

## Solutions

## Python

``` python
def combinationSum4(self, nums: List[int], target: int) -> int:
    dp = [0 for _ in range(target + 1)]
    dp[0] = 1
    for i in range(1, target + 1):
        for num in nums:
            if i - num >= 0:
                dp[i] += dp[i - num]
    return dp[-1]
```

## Go

``` go
func combinationSum4(nums []int, target int) int {
    dp := make([]int, target + 1)
    dp[0] = 1
    for i := 1; i < target + 1; i++ {
        for _, num := range nums {
            if i - num >= 0 {
                dp[i] += dp[i - num]
            }
        }
    }
    return dp[target]
}
```

## Rust

``` rust
pub fn combination_sum4(nums: Vec<i32>, target: i32) -> i32 {
    let mut dp = vec![0; (target + 1) as usize];
    dp[0] = 1;
    for i in 1..target + 1 {
        for num in &nums {
            if i - num >= 0 {
                dp[i as usize] += dp[(i - num) as usize];
            }
        }
    }
    dp[target as usize]
}
```
