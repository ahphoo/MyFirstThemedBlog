+++
title="Two Sum"
date=2020-05-09
+++

## Problem Link

[https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)

## How to solve

Let **a** and **b** be two numbers that sum to **c**. Algebraically, **a** and **b** ,

**a = c - b** 

**b = c - a**

You want to return the indices of two numbers that sum to c, that is, a and b. Let's say while iterating through the array nums, you see **a**. You want to remember the index of **a** so that if you see **b** (or equivalently **c - a**), you can return an array with their indices. We can "remember" the index of **a** by putting a **a** and it's index as a key-value pair into a dictionary.

## Complexity Analysis

## Time: O(N)

We iterate through all N integers in the nums array.

## Space: O(N)

For every i, we put the complement of nums[i] in our hash table.

## Solutions

## Python

``` python
def twoSum(self, nums: List[int], target: int) -> List[int]:
    complements = {}
    for i in range(len(nums)):
        if target - nums[i] in complements:
            return [i, complements[target - nums[i]]]
        complements[nums[i]] = i
```

## Go

``` go
func twoSum(nums []int, target int) []int {
    complements := make(map[int]int)
    for i := 0; i < len(nums); i++ {
        if val, key_exists := complements[target - nums[i]]; key_exists {
            return []int{ i, val }
        }
        complements[nums[i]] = i
    }
    return []int{}
}
```

## Rust

``` rust
use std::collections::HashMap;

impl Solution {
    pub fn two_sum(nums: Vec<i32>, target: i32) -> Vec<i32> {
        let mut num_to_index = HashMap::with_capacity(nums.len());

        for (i, num) in nums.iter().enumerate() {
            match num_to_index.get(&(target - num)) {
                Some(complement) => return vec![*complement as i32, i as i32],
                None => num_to_index.insert(num, i)
            };  
        }
        vec![]
    }
}
```
