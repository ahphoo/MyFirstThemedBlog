+++
title="Jump Game"
date=2020-05-24
+++

## Problem Link

[https://leetcode.com/problems/jump-game/](https://leetcode.com/problems/jump-game/)

## How to solve

Iterate through each index in `nums` and check if we can reach the last index. Let `i` be the current index.

1. If `i` is greater than the maximum reacheable index, we cannot reach the end of the `nums` array from index `0`. Return false.

2. If you can jump to a farther index at index `i`, update the maximum reacheable index to `i + nums[i]`.

If we manage to iterate through all indices in `nums`, this means we were able to reach the last index starting from index `0`. Hence, we return true.

## Complexity Analysis

## Time: O(N)

In the worst case, we have to iterate through all indices in the `nums` array.

## Space: O(1)

We keep a temp variable to keep track of the maximum reacheable index.

## Solutions

## Python

``` python
def canJump(self, nums: List[int]) -> bool:
    max_idx = 0

    for i in range(len(nums)):
        if i > max_idx:
            return False

        max_idx = max(max_idx, i + nums[i])

    return True
```

## Go

``` go
func canJump(nums []int) bool {
    max_idx := 0

    for i := range nums {
        if i > max_idx {
            return false
        }
        if i + nums[i] > max_idx {
            max_idx = i + nums[i]
        }
    }
    return true
}
```

## Rust

``` rust
use std::cmp::max;

impl Solution {
    pub fn can_jump(nums: Vec<i32>) -> bool {
        let mut max_idx = 0;

        for i in 0..nums.len() {
            if i > max_idx {
                return false;
            }
            max_idx = max(max_idx, i + nums[i] as usize);
        }
        true
    }
}
```
