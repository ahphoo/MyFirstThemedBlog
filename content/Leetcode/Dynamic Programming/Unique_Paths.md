+++
title="Unique Paths"
date=2020-05-23
+++

## Problem Link

[https://leetcode.com/problems/unique-paths/](https://leetcode.com/problems/unique-paths/)

## How to solve

Let N be the number of rows, and M be the number of columns. If N == 1, then there is only one unique path to get to the bottom-rightmost cell (the robot can only go right). Similarly if M == 1, then there is only one unique path to get the bottom-rightmost cell (the robot can only go down).

Let's denote a cell on row `i` and col `j` by `grid[i][j]`. Since the robot starts from the top-leftmost corner, it can arrive at `grid[i][j]` by at most two directions, from above or to the left (`grid[i - 1][j]` and `grid[i][j - 1]`). If we know the number of unique paths above and to the left of `grid[i][j]`, the number of unqiue paths to `grid[i][j]` is simply their sum.

## Complexity Analysis

## Time: O(N * M)

We traverse through the grid, calculating the number of unique paths for each cell.

## Space: O(N * M)

We create a 2-D array of cells with N rows and M columns.

Note, the space can be further reduced to O(M). It isn't necessary to record the number of unique paths for __every__ cell in the grid. We can keep track of the number of unique paths for 2 rows at a time, since the number of unique paths for any given cell only depends on the number of unique paths from the cell above, and the cell to left.

## Solutions

## Python

``` python
    if m == 1 or n == 1:
        return 1

    unique_paths = [[0 for _ in range(m)] for _ in range(2)]

    for i in range(2):
        unique_paths[i][0] = 1

    for j in range(m):
        unique_paths[0][j] = 1

    for i in range(1, n):
        for j in range(1, m):
            unique_paths[i % 2][j] = unique_paths[i % 2 - 1][j] + unique_paths[i % 2][j - 1]

    return unique_paths[-1][-1] if n % 2 == 0 else unique_paths[0][-1]
```

## Go

``` go
func uniquePaths(m int, n int) int {
    dp := make([][]int, n)

    for i := range dp {
        dp[i] = make([]int, m)
        dp[i][0] = 1
    }

    for j := range dp[0] {
        dp[0][j] = 1
    }

    for i := 1; i < n; i++ {
        for j := 1; j < m; j++ {
            dp[i][j] = dp[i - 1][j] + dp[i][j - 1]
        }
    }

    return dp[n - 1][m - 1]
}
```

## Rust

``` rust
pub fn unique_paths(m: i32, n: i32) -> i32 {
    let n = n as usize;
    let m = m as usize;
    let mut dp = vec![vec![1; m]; n];

    for i in 1..n {
        for j in 1..m {
            dp[i][j] = dp[i - 1][j] + dp[i][j - 1];
        }
    }

    dp[n - 1][m - 1]
}
```
