+++
title="Contains Duplicate"
date=2020-05-10

[taxonomies]
tags = ["Array"]
authors = ["Allan Phu"]
+++

## Problem Link

[https://leetcode.com/problems/contains-duplicate/submissions/](https://leetcode.com/problems/contains-duplicate/submissions/)

## How to solve

We iterate through the nums array and check if a number has been seen more than once. To remember numbers that we've already seen, we can store numbers in a hash set (python and rust) or a hash table (go). If we see a number that's already present in our hash set/hash table, we know that that number is a duplicate. If we iterate through all numbers without seeing a duplicate, that must mean all numbers in the nums array are distinct.

## Complexity Analysis

## Time: O(N)

We have to check all **N** numbers in the nums array for duplicates.

## Space: O(N)

In the worst case, all numbers are distinct, so we will insert all **N** elements into the hash set/ hash table.

## Solutions

## Python

``` python
def containsDuplicate(self, nums: List[int]) -> bool:
    dups = set()
    for num in nums:
        if num in dups:
            return True
        dups.add(num)
    return False
```

## Go

``` go
func containsDuplicate(nums []int) bool {
    set := make(map[int]bool)
    for _, num := range nums {
        in_set := set[num]
        if in_set {
            return true
        }
        set[num] = true
    }
    return false
}
```

## Rust

``` rust
use std::collections::HashSet;

impl Solution {
    pub fn contains_duplicate(nums: Vec<i32>) -> bool {
        let mut set = HashSet::with_capacity(nums.len());

        for &num in &nums {
            if set.contains(&num) {
                return true;
            }
            set.insert(num);
        }

        false
    }
}
```
