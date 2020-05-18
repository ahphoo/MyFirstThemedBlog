+++
title="Longest Increasing Subsequence"
date=2020-05-18
+++

## Problem Link

[https://leetcode.com/problems/longest-increasing-subsequence/](https://leetcode.com/problems/longest-increasing-subsequence/)

## How to solve

We create an array, `lis`, to hold the numbers of the longest increasing sequence. For every number `num` in `nums`, we check if `lis` is empty or if `num` is greater than the last element of `lis`. In either case, we append `num` to `lis`. If `num` is less than or equal to the last element of `lis`, we use binary search to find the correct spot to insert the element into `lis`.

## Complexity Analysis

## Time: O(N log N)

We iterate through all N numbers. If a number is less than or equal to the last element in our increasing subsequence list, we use binary search to find the correct place to insert it.

## Space: O(N)

In the worst case, if `nums` is sorted in increasing order, `lis` holds all the numbers of `nums`.

## Solutions

## Python

``` python
if not nums:
    return 0

lis = []

for num in nums:
    if not lis or num > lis[-1]:
        lis.append(num)
    else:
        lo = 0
        hi = len(lis) - 1

        while lo <= hi:
            mid = lo + (hi - lo) // 2
            if num > lis[mid]:
                lo = mid + 1
            else:
                hi = mid - 1

        lis[lo] = num

return len(lis)
```

## Go

``` go
func lengthOfLIS(nums []int) int {
    if len(nums) == 0 {
        return 0
    }

    lis := make([]int, 0)

    for _, num := range nums {
        if len(lis) == 0 || num > lis[len(lis) - 1] {
            lis = append(lis, num)
        } else {
            lo := 0
            hi := len(lis) - 1

            for lo <= hi {
                mid := lo + (hi - lo) / 2
                if num > lis[mid] {
                    lo = mid + 1
                } else {
                    hi = mid - 1
                }
            }
            lis[lo] = num
        }
    }
}
```

## Rust

``` rust
pub fn length_of_lis(nums: Vec<i32>) -> i32 {
    if nums.len() == 0 {
        return 0;
    }

    let mut lis = Vec::new();

    for num in &nums {
        if lis.len() == 0 || num > lis[lis.len() - 1] {
            lis.push(num);
        } else {
            let mut lo = 0 as i32;
            let mut hi = (lis.len() - 1) as i32;

            while lo <= hi {
                let mid = (lo + (hi - lo) / 2) as usize;
                if num > lis[mid] {
                    lo = (mid + 1) as i32;
                } else {
                    hi = (mid - 1) as i32;
                }
            }
            lis[lo as usize] = num
        }
    }

    lis.len() as i32
}
```
