+++
title="Missing Number"
date=2020-05-14
+++

## Problem Link

[https://leetcode.com/problems/missing-number/](https://leetcode.com/problems/missing-number/)

## How to solve

## Complexity Analysis

## Time: O(n)

## Space: O(1)

## Solutions

## Python

``` python
def missingNumber(self, nums: List[int]) -> int:
    missing = len(nums)

    for i, num in enumerate(nums):
        missing ^= i ^ num

    return missing
```

## Go

``` go
func missingNumber(nums []int) int {
    missing := len(nums)

    for i, num := range nums {
        missing ^= i ^ num
    }

    return missing
}
```

## Rust

``` rust
pub fn missing_number(nums: Vec<i32>) -> i32 {
    let mut missing = nums.len() as i32;

    for (i, &num) in nums.iter().enumerate() {
        missing ^= (i as i32) ^ num;
    }

    missing
}
```
