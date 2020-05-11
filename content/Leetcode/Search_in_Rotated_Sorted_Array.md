+++
title="Search in Rotated Sorted Array"
date=2020-05-11
+++

## Problem Link

[https://leetcode.com/problems/search-in-rotated-sorted-array/submissions/](https://leetcode.com/problems/search-in-rotated-sorted-array/submissions/)

## How to solve

## Complexity Analysis

## Time: O(log N)

Binary search will find the minimum element in at most log N iterations.

## Space: O(1)

We use two local variables to keep track of the lower and upper bound of the binary search.

## Solutions

## Python

``` python
def search(self, nums: List[int], target: int) -> int:
    if not nums:
        return -1

    lo = 0
    hi = len(nums) - 1

    while lo <= hi:
        mid = lo + (hi - lo) // 2
        if nums[mid] == target:
            return mid
        elif nums[lo] <= nums[mid]:
            if nums[lo] <= target < nums[mid]:
                hi = mid - 1
            else:
                lo = mid + 1
        elif nums[mid] <= nums[hi]:
            if nums[mid] < target <= nums[hi]:
                lo = mid + 1
            else:
                hi = mid - 1

    return -1
```

## Go

``` go
func search(nums []int, target int) int {
    if nums == nil {
        return -1
    }

    var lo int = 0
    var hi int = len(nums) - 1

    for lo <= hi {
        var mid int = lo + (hi - lo) / 2
        if nums[mid] == target {
            return mid
        } else if nums[lo] <= nums[mid] {
            if nums[lo] <= target && target < nums[mid] {
                hi = mid - 1
            } else {
                lo = mid + 1
            }
        } else if nums[mid] <= nums[hi] {
            if nums[mid] < target && target <= nums[hi] {
                lo = mid + 1
            } else {
                hi = mid - 1
            }
        }
    }
    return -1
}
```

## Rust

``` rust
use std::usize::MAX;

impl Solution {
    pub fn search(nums: Vec<i32>, target: i32) -> i32 {
        if nums.len() == 0 {
            return -1;
        }

        let mut lo = 0;
        let mut hi = nums.len() - 1;

        while hi != MAX && lo <= hi {
            let mid = lo + (hi - lo) / 2;
            if nums[mid] == target {
                return mid as i32;
            } 
            else if nums[lo] <= nums[mid] {
                if nums[lo] <= target && target < nums[mid] {
                    hi = mid - 1;
                } else {
                    lo = mid + 1;
                }
            }
            else if nums[mid] <= nums[hi] {
                if nums[mid] < target && target <= nums[hi] {
                    lo = mid + 1;
                } else {
                    hi = mid - 1;
                }
            }
        } 
        -1
    }
}
```
