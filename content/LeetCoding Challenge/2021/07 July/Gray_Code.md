+++
title="Gray Code"
date=2020-07-01
+++

## Problem Link

[https://leetcode.com/problems/gray-code/](https://leetcode.com/problems/gray-code/)

## How to solve

## Complexity Analysis

## Time: O(N)

## Space: O(N)

## Solutions

## Python

``` python
def grayCode(self, n: int) -> List[int]:
    result = [0]
    used = set(result)
    self.grayCodeHelper(result, used, n)
    return result
    
def grayCodeHelper(self, result, used, n):
    # 1 << n is the same as 1 * 2**n
    if len(result) == (1 << n):
        return True
    
    for i in range(n):
        mask = 1 << i
        word = result[-1] ^ mask
        
        if word in used:
            continue
            
        result.append(word)
        used.add(word)
        
        if self.grayCodeHelper(result, used, n):
            return True
        
        result = result[:-1]
        used.remove(word)
        
    return False
```

## Go

## Rust
