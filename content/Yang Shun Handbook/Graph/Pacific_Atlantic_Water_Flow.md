+++
title="Pacific Atlantic Water Flow"
date=2020-06-06

[taxonomies]
tags = ["Graph"]
authors = ["Allan Phu"]
+++

## Problem Link

[https://leetcode.com/problems/pacific-atlantic-water-flow/](https://leetcode.com/problems/pacific-atlantic-water-flow/)

## How to solve

## Complexity Analysis

## Time

## Space

## Solutions

## Python

``` python
def pacificAtlantic(self, matrix: List[List[int]]) -> List[List[int]]:
    if not matrix:
        return []

    rows = len(matrix)
    cols = len(matrix[0])

    pacific = [[False for _ in range(cols)] for _ in range(rows)]
    atlantic = [[False for _ in range(cols)] for _ in range(rows)]

    def can_reach_ocean(ocean, i, j):
        ocean[i][j] = True

        if i > 0 and matrix[i - 1][j] >= matrix[i][j] and not ocean[i - 1][j]:
            can_reach_ocean(ocean, i - 1, j)
        if i < rows - 1 and matrix[i + 1][j] >= matrix[i][j] and not ocean[i + 1][j]:
            can_reach_ocean(ocean, i + 1, j)
        if j > 0 and matrix[i][j - 1] >= matrix[i][j] and not ocean[i][j - 1]:
            can_reach_ocean(ocean, i, j - 1)
        if j < cols - 1 and matrix[i][j + 1] >= matrix[i][j] and not ocean[i][j + 1]:
            can_reach_ocean(ocean, i, j + 1)

    for i in range(rows):
        can_reach_ocean(pacific, i, 0)
        can_reach_ocean(atlantic, i, cols - 1)

    for j in range(cols):
        can_reach_ocean(pacific, 0, j)
        can_reach_ocean(atlantic, rows - 1, j)

    ans = []
    for i in range(rows):
        for j in range(cols):
            if pacific[i][j] and atlantic[i][j]:
                ans.append([i, j])

    return ans
```

## Go

``` go

```

## Rust

``` rust

```
