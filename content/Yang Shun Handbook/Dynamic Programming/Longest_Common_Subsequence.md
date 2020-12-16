+++
title="Longest Common Subsequence"
date=2020-05-18

[taxonomies]
tags = ["Dynamic Programming"]
authors = ["Allan Phu"]
+++

## Problem Link

[https://leetcode.com/problems/longest-increasing-subsequence/](https://leetcode.com/problems/longest-increasing-subsequence/)

## How to solve

Create a two-dimensional array of integers `dp`, where `dp[i][j]` represents the longest common subsequence between a substring of text1 from `0` to `i` and a substring of text2 from `0` to `j`. The length of the longest common subsequence of text1 and text2 is the last element in `dp`.

## Complexity Analysis

## Time: O(text1 * text2)

For every character in text1, we check all substrings of text2.

## Space: O(text1 * text2)

We have a two-dimensional dp array of size len(text1) * len(text2).

## Solutions

## Python

``` python
rows = len(text1)
cols = len(text2)

dp = [[0 for _ in range(cols + 1)] for _ in range(rows + 1)]

for i in range(1, rows + 1):
    for j in range(1, cols + 1):
        if text1[i - 1] == text2[j - 1]:
            dp[i][j] = dp[i-1][j-1] + 1
        else:
            dp[i][j] = max(dp[i-1][j], dp[i][j-1])

return dp[-1][-1]
```

## Go

``` go
func longestCommonSubsequence(text1 string, text2 string) int {
    rows := len(text1) + 1
    cols := len(text2) + 1

    dp := make([][]int, rows)
    for i := range dp {
        dp[i] = make([]int, cols)
    }

    for i := 1; i < rows; i++ {
        for j := 1; j < cols; j++ {
            if text1[i - 1] == text2[j - 1] {
                dp[i][j] = dp[i - 1][j - 1] + 1
            } else if dp[i][j - 1] > dp[i - 1][j] {
                dp[i][j] = dp[i][j - 1]
            } else {
                dp[i][j] = dp[i - 1][j]
            }
        }
    }

    return dp[rows - 1][cols - 1]
}
```

## Rust

``` rust
pub fn longest_common_subsequence(text1: String, text2: String) -> i32 {
    let rows = text1.len() + 1;  // len() returns number of bytes in String, not necessarily
    let cols = text2.len() + 1;  // the number of chars!

    let mut dp_row = vec![0; cols];
    let mut dp = vec![dp_row; rows];

    let txt1 = text1.as_bytes(); // Convert to &[u8] to index into String
    let txt2 = text2.as_bytes();

    for i in 1..rows {
        for j in 1..cols {
            if txt1[i - 1] == txt2[j - 1] {
                dp[i][j] = dp[i - 1][j - 1] + 1;
            } else if dp[i - 1][j] > dp[i][j - 1] {
                dp[i][j] = dp[i - 1][j];
            } else {
                dp[i][j] = dp[i][j - 1];
            }
        }
    }
  
    dp[rows - 1][cols - 1] as i32
}
```
