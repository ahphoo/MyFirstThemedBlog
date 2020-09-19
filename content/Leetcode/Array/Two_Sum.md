+++
title="Two Sum"
date=2020-05-09

[taxonomies]
tags = ["Array"]
authors = ["Allan Phu"]
+++

## Problem Link

[https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)

## How to solve

We iterate through the integers in the array, checking if we have seen it's complement in the array before.

We store the complement and it's array index in a hashmap.

There are two different ways to check if the complement is in the array.

1. For each `num` in the array, check if `target - num` is in the hashmap.
2. For each `num`, calculate `target - num` and check if `num` is in the hashmap.


If the complement is not in the hashmap, we save the current integer and it's array index in the hashmap.

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

## Java

``` java
public int[] twoSum(int[] nums, int target) {
    HashMap<Integer, Integer> complement = new HashMap<>();
    for (int i = 0; i < nums.length; i++) {
        if (complement.containsKey(target - nums[i])) {
            return new int[] {i, complement.get(target - nums[i])};
        }
        complement.put(nums[i], i);
    }
    return new int[] {-1, -1};
}
```
