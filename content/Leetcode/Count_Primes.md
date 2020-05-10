+++
title="Count Primes"
date=2020-05-09
+++

## Problem Link

[https://leetcode.com/problems/count-primes/](https://leetcode.com/problems/count-primes/)

## How to solve

## Complexity Analysis

## Time: O(N log log N)

## Space: O(N)

## Solutions

## Python

``` python
def countPrimes(self, n: int) -> int:
    primes = []
    is_prime = [False, False] + [True for _ in range(n - 1)]

    for i in range(2, len(is_prime)):
        if is_prime[i]:
            if i != n:
                primes.append(i)
            for j in range(i, len(is_prime), i):
                is_prime[j] = False

    return len(primes)
```

## Go

## Rust
