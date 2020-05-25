+++
title="Counting Bits"
date=2020-05-14

[taxonomies]
tags = ["Binary"]
authors = ["Allan Phu"]
+++

## Problem Link

[https://leetcode.com/problems/counting-bits/](https://leetcode.com/problems/counting-bits/)

## How to solve

Create an array of size `num + 1` to keep track of the number of ones for each number from 0 to `num`. In a for-loop, for each number `i`, turn off it's rightmost set bit and count the number of ones it has left. Add one to that result (because we turned off the rightmost set bit) and save the result in the array.

## Complexity Analysis

## Time: O(n)

We iterate through `N - 1` numbers and count the number of ones they have.

## Space: O(n)

We store the counts of each number from `0` to `N` in an array.

## Solutions

## Python

``` python
def countBits(self, num: int) -> List[int]:
    count = [0 for _ in range(num + 1)]

    for i in range(1, num + 1):
        count[i] = count[i & (i - 1)] + 1

    return count
```

## Go

``` go
func countBits(num int) []int {
    count := make([]int, num + 1)

    for i := 1; i < num + 1; i++ {
        count[i] = count[i & (i - 1)] + 1
    }

    return count
}
```

## Rust

``` rust
pub fn count_bits(num: i32) -> Vec<i32> {
    let mut count: Vec<i32> = vec![0; (num + 1) as usize];

    for i in 1..count.len() {
        count[i] = count[i & (i - 1)] + 1;
    }

    count
}
```
