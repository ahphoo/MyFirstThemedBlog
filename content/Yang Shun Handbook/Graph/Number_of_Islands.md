+++
title="Number of Islands"
date=2020-06-06

[taxonomies]
tags = ["Graph"]
authors = ["Allan Phu"]
+++

## Problem Link

[https://leetcode.com/problems/number-of-islands/](https://leetcode.com/problems/number-of-islands/)

## How to solve

## Complexity Analysis

## Time

## Space

## Solutions

## Python

``` python
# O(mn) time | O(mn) space
def numIslands(self, grid: List[List[str]]) -> int:
    rows = len(grid)
    cols = len(grid[0])
    num_islands = 0
    
    for i in range(rows):
        for j in range(cols):
            if grid[i][j] == "1":
                self.removeIsland(i, j, grid)
                num_islands += 1
    
    return num_islands

def removeIsland(self, i, j, grid):
    if grid[i][j] == "1":
        grid[i][j] = 0
        
        if i > 0:
            self.removeIsland(i - 1, j, grid)
        if i < len(grid) - 1:
            self.removeIsland(i + 1, j, grid)
        if j > 0:
            self.removeIsland(i, j - 1, grid)
        if j < len(grid[0]) - 1:
            self.removeIsland(i, j + 1, grid)
```

Iterative BFS solution

```python
# O(mn) time | O(mn) space
def numIslands(self, grid: List[List[str]]) -> int:
    rows = len(grid)
    cols = len(grid[0])
    num_islands = 0
    
    for i in range(rows):
        for j in range(cols):
            if grid[i][j] == "1":
                self.removeIsland(i, j, grid)
                num_islands += 1
    
    return num_islands

def removeIsland(self, row, col, grid):
    stack = [(row, col)]
    
    while stack:
        i, j = stack.pop()
        
        if self.isLand(i, j, grid):
            grid[i][j] = "0"
            stack.append((i - 1, j))
            stack.append((i + 1, j))
            stack.append((i, j - 1))
            stack.append((i, j + 1))
            
def isLand(self, i, j, grid):
    valid_row = 0 <= i < len(grid)
    valid_col = 0 <= j < len(grid[0])
    return valid_row and valid_col and grid[i][j] == "1"
```

## Go

``` go

```

## Rust

``` rust

```
