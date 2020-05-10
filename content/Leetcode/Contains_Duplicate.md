+++
title="Contains Duplicate"
date=2020-05-10
+++

# Problem Link
[https://leetcode.com/problems/contains-duplicate/submissions/](https://leetcode.com/problems/contains-duplicate/submissions/)
# How to solve

# Complexity Analysis

## Time: O(N)

## Space: O(N)

# Solutions

## Python
```
dups = set()
for num in nums:
    if num in dups:
        return True
    dups.add(num)
return False
```

## Go
```
```

## Rust
```
```