+++
title="Product of Array Except Self"
date=2020-05-10
+++

## Problem Link

[https://leetcode.com/problems/product-of-array-except-self/](https://leetcode.com/problems/product-of-array-except-self/)

## How to solve

Suppose we have a number `i`. Notice that the product of all numbers except `i` is equal to the product of all numbers to the left of `i` multiplied by the product of all numbers to the right of `i`. For example, let the array nums = [1,2,3,4]. For every number `i`, calculate the product of all numbers to the left of `i`. We have the array:

L = [1, 1, 2, 6]

To calculate the product of all numbers to the right of `i`, we don't need to create another array. Instead, we keep a variable `R` that represents the running-product of all elements to the right of `i`. Iterating through the array backwards, for every index `j`, we multiply `L[j]` by `R` to get the product of all numbers except `nums[j]`. We update our running-product `R` by mulitiplying it by `nums[j]`.

## Complexity Analysis

## Time: O(N)

We iterate through the nums array twice, which is `O(2n) = O(n)`. First, to create an array `L` which holds the products of all elements to the left of index `i`. Second, we iterate through `L` backwards, updating each index to hold the product of all numbers except nums[i] for all `i`.

## Space: O(N)

We create an array `L` of size N.

## Solutions

## Python

``` python
def productExceptSelf(self, nums: List[int]) -> List[int]:
    L = [1 for _ in range(len(nums))]

    for i in range(1, len(nums)):
        L[i] = nums[i - 1] * L[i - 1]

    ans = L
    R = 1
    for j in range(len(nums) - 1, -1, -1):
        ans[j] *= R
        R *= nums[j]

    return ans
```

## Go

``` go
func productExceptSelf(nums []int) []int {
    L := make([]int, len(nums))
    for i := range L {
        L[i] = 1
    }

    for j := 1; j < len(nums); j++ {
        L[j] = nums[j - 1] * L[j - 1]
    }

    ans := L
    R := 1
    for k := len(nums) - 1; k > -1; k-- {
        ans[k] *= R
        R *= nums[k]
    }

    return ans
}
```

## Rust

``` rust
pub fn product_except_self(nums: Vec<i32>) -> Vec<i32> {
    let mut L = vec![1; nums.len()];

    for i in 1..nums.len() {
        L[i] = nums[i - 1] * L[i - 1];
    }

    let mut ans = L;
    let mut R: i32 = 1;
    for j in (0..nums.len()).rev() {
        ans[j] *= R;
        R *= nums[j];
    }

    ans
}
```
