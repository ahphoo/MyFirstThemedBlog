+++
title="Trapping Rain Water"
date=2020-06-20

[taxonomies]
tags = ["Array"]
authors = ["Allan Phu"]
+++

## Problem Link

[https://leetcode.com/problems/trapping-rain-water/](https://leetcode.com/problems/trapping-rain-water/)

## How to solve

## Complexity Analysis

## Time: O(N)

## Space: O(1)

## Solutions

## Python

``` python
def trap(self, height: List[int]) -> int:
    left = 0
    right = len(height) - 1

    left_max = 0
    right_max = 0

    total = 0
    while left < right:
        if height[left] <= height[right]:
            if height[left] >= left_max:
                left_max = height[left]
            else:
                total += left_max - height[left]
            left += 1
        else:
            if height[right] >= right_max:
                right_max = height[right]
            else:
                total += right_max - height[right]
            right -= 1

    return total
```

## Go

``` go
left := 0
right := len(height) - 1

left_max := 0
right_max := 0

total := 0
for left < right {
    if height[left] <= height[right] {
        if height[left] >= left_max {
            left_max = height[left]
        } else {
            total += left_max - height[left]
        }
        left += 1
    } else {
        if height[right] >= right_max {
            right_max = height[right]
        } else {
            total += right_max - height[right]
        }
        right -= 1
    }
}

return total
```

## Rust

``` rust
pub fn trap(height: Vec<i32>) -> i32 {
    if height.len() == 0 {
        println!("{}", height.len() - 1);
        return 0;
    }

    let mut left = 0;
    let mut right = height.len() - 1;

    let mut left_max = 0;
    let mut right_max = 0;

    let mut total = 0;

    while left < right {
        if height[left] <= height[right] {
            if height[left] >= left_max {
                left_max = height[left]
            } else {
                total += left_max - height[left]
            }
            left += 1
        } else {
            if height[right] >= right_max {
                right_max = height[right]
            } else {
                total += right_max - height[right]
            }
            right -= 1
        }
    }

    total
}
```
