+++
title="Find Minimum in Rotated Sorted Array"
date=2020-05-11
+++

## Problem Link

[https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)

## How to solve

Check if the first number is less than the last number. If true, this means the sorted array has not been rotated. Do binary search on the array, starting with `lo = 0` and `hi = index of last element`. In each iteration of the binary search, we check if we've seen the rotation point (the `mid-1` > `mid` or `mid` > `mid-1`). If we're not at a rotation point, then we check if `mid` is in the non-rotated part of the array, and update lo and hi accordingly.

## Complexity Analysis

## Time: O(log N)

Binary search will find the minimum element in at most log N iterations.

## Space: O(1)

We use two local variables to keep track of the lower and upper bound of the binary search.

## Solutions

## Python

``` python
def findMin(self, nums: List[int]) -> int:
    if nums[0] < nums[-1]:
        return nums[0]

    lo = 0
    hi = len(nums) - 1

    while lo <= hi:
        mid = lo + (hi - lo) // 2
        if mid - 1 >= 0 and nums[mid - 1] > nums[mid]:
            return nums[mid]
        elif mid + 1 < len(nums) and nums[mid] > nums[mid + 1]:
            return nums[mid + 1]
        elif nums[0] < nums[mid]:
            lo = mid + 1
        else:
            hi = mid - 1

    return nums[lo]
```

## Go

``` go
func findMin(nums []int) int {
    if nums[0] < nums[len(nums) - 1] {
        return nums[0]
    }

    var lo int = 0
    var hi int = len(nums) - 1

    for lo < hi {
        var mid int = lo + (hi - lo) / 2
        if nums[mid] > nums[mid + 1] {
            return nums[mid + 1]
        }
        if nums[mid - 1] > nums[mid] {
            return nums[mid]
        }
        if nums[0] < nums[mid] {
            lo = mid + 1
        } else {
            hi = mid
        }
    }

    return nums[lo]
}
```

## Rust

``` rust
pub fn find_min(nums: Vec<i32>) -> i32 {
    if nums[0] < nums[nums.len() - 1] {
        return nums[0];
    }

    let mut lo = 0;
    let mut hi = nums.len() - 1;

    while lo < hi {
        let mid = lo + (hi - lo) / 2;
        if nums[mid] > nums[mid + 1] {
            return nums[mid + 1];
        }
        if nums[mid - 1] > nums[mid] {
            return nums[mid];
        }
        if nums[0] < nums[mid] {
            lo = mid + 1;
        } else {
            hi = mid;
        }
    }
    nums[lo]
}
```
