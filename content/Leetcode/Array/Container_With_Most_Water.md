+++
title="Container_With_Most_Water"
date=2020-05-11

[taxonomies]
tags = ["Array"]
authors = ["Allan Phu"]
+++

## Problem Link

[https://leetcode.com/problems/container-with-most-water/](https://leetcode.com/problems/container-with-most-water/)

## How to solve

Note that the amount of water a container can hold is determined by the length of the shorter side. Using two pointers, we keep track of the maximum amount of water given pair of lines can hold. While the pointers have not crossed each other, we increment the pointer to the shorter line, in hope of finding a longer line to maximize the amount of water the container can hold.

## Complexity Analysis

## Time: O(N)

We check all pairs of l, r, starting l from the leftmost line and r from the rightmost line.

## Space: O(1)

We use constant space.

## Solutions

## Python

``` python
def maxArea(self, height: List[int]) -> int:
    maxArea = 0

    l = 0
    r = len(height) - 1
    while l < r:
        if height[l] < height[r]:
            maxArea = max(maxArea, height[l] * (r - l))
            l += 1
        else:
            maxArea = max(maxArea, height[r] * (r - l))
            r -= 1
    return maxArea
```

## Go

``` go
func maxArea(height []int) int {
    max_area := 0

    l := 0
    r := len(height) - 1

    for l < r {
        if height[l] < height[r] {
            if max_area < (height[l] * (r - l)) {
                max_area = height[l] * (r - l)
            }
            l += 1
        } else {
            if max_area < (height[r] * (r - l)) {
                max_area = height[r] * (r - l)
            }
            r -= 1
        }
    }

    return max_area
}
```

## Rust

``` rust
use std::cmp::max;

impl Solution {
    pub fn max_area(height: Vec<i32>) -> i32 {
        let mut maxArea: i32 = 0;
        let mut l = 0;
        let mut r = height.len() - 1;

        while l < r {
            if height[l] < height[r] {
                maxArea = max(maxArea, height[l] * ((r-l) as i32));
                l += 1;
            } else {
                maxArea = max(maxArea, height[r] * ((r-l) as i32));
                r -= 1;
            }
        }

        maxArea
    }
}
```
