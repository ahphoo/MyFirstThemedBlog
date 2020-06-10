+++
title="Maximal Rectangle"
date=2020-06-20

[taxonomies]
tags = ["Array"]
authors = ["Allan Phu"]
+++

## Problem Link

[https://leetcode.com/problems/maximal-rectangle/](https://leetcode.com/problems/maximal-rectangle/)

## How to solve

## Complexity Analysis

## Time: O(MN)

## Space: O(N)

## Solutions

## Python

``` python
def maximalRectangle(self, matrix: List[List[str]]) -> int:
    if not matrix:
        return 0

    rows = len(matrix)
    cols = len(matrix[0])

    height = [0 for _ in range(cols)]
    left   = [0 for _ in range(cols)]
    right  = [cols - 1 for _ in range(cols)]

    max_area = 0

    for i in range(rows):

        for j in range(cols):
            if matrix[i][j] == '1':
                height[j] += 1
            else:
                height[j] = 0

        cur_left = 0

        for j in range(cols):
            if matrix[i][j] == '1':
                left[j] = max(left[j], cur_left)
            else:
                left[j] = 0
                cur_left = j + 1

        cur_right = cols - 1

        for j in range(cols - 1, -1, -1):
            if matrix[i][j] == '1':
                right[j] = min(right[j], cur_right)
            else:
                right[j] = cols - 1
                cur_right = j - 1

        for j in range(cols):
            max_area = max(max_area, height[j] * (right[j] - left[j] + 1))

    return max_area
```
