+++
title="House Robber II"
date=2020-05-19
+++

## Problem Link

[https://leetcode.com/problems/house-robber-ii/](https://leetcode.com/problems/house-robber-ii/)

## How to solve

## Complexity Analysis

## Time: O(N)

## Space: O(1)

## Solutions

## Python

``` python
def rob(self, nums: List[int]) -> int:
    if not nums:
        return 0
    if len(nums) < 4:
        return max(nums)

    def houseRobber(start, end):
        two_houses_ago = 0
        one_house_ago = 0
        for i in range(start, end):
            two_houses_ago, one_house_ago = one_house_ago, \
                                            max(one_house_ago, nums[i] + two_houses_ago)
        return one_house_ago

    max_first_house = houseRobber(0, len(nums) - 1)
    max_second_house = houseRobber(1, len(nums))

    return max(max_first_house, max_second_house)
```

## Go

``` go
func rob(nums []int) int {
    switch length := len(nums); length {
    case 0:
        return 0
    case 1:
        return nums[0]
    case 2:
        return max(nums[0], nums[1])
    case 3:
        return max(nums[0], max(nums[1], nums[2]))
    }

    max_first_house := houseRobber(nums, 0, len(nums) - 1)
    max_second_house := houseRobber(nums, 1, len(nums))

    if max_first_house > max_second_house {
        return max_first_house
    }
    return max_second_house
}

func houseRobber(nums []int, start int, end int) int {
    two_houses_ago := 0
    one_house_ago := 0
    for i := start; i < end; i++ {
        two_houses_ago, one_house_ago = one_house_ago, max(one_house_ago, nums[i] + two_houses_ago)
    }
    return one_house_ago
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
        }
        else if nums.len() <= 3 {
            match nums.iter().max() {
                Some(&length) => return length,
                None => return 0
            }
        }

        let mut two_houses_ago = 0;
        let mut one_house_ago = 0;
        for i in 0..nums.len() - 1 {
            let temp = two_houses_ago;
            two_houses_ago = one_house_ago;
            one_house_ago = max(one_house_ago, nums[i] + temp);
        }

        let max_first_house = one_house_ago;

        two_houses_ago = 0;
        one_house_ago = 0;
        for i in 1..nums.len() {
            let temp = two_houses_ago;
            two_houses_ago = one_house_ago;
            one_house_ago = max(one_house_ago, nums[i] + temp);
        }

        max(max_first_house, one_house_ago)
    }
}
```
