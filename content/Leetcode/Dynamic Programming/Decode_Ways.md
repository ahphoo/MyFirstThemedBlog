+++
title="Decode Ways"
date=2020-05-21
+++

## Problem Link

[https://leetcode.com/problems/decode-ways/](https://leetcode.com/problems/decode-ways/)

## How to solve

To make things simpler, let's start with the case where `s` is a string of length `1`. There is only one way to decode `s`, which is to interpret it as a single character if `s[0]` is between `1` and `9` inclusive. We can't decode `s` if `s[0]` is `0` because letters are mapped starting from `A -> 1` to `Z -> 26`. Hence, there is at most `1` way to decode `s`.

When `s` is of length `2`, we can decode each character individually the same way as we did when `s` was of length `1`. Also, we can check if decoding both numbers together yields a valid letter. Specifically, if the integer formed by concatenating `s[0]` and `s[1]` is between `10` and `26` inclusive, we can decode them as a single letter. Hence, there are at most `2` ways to decode `s`.

When `s` is of length `3`, we repeat the above steps to decode `s`. Note that we aren't adding any new ways to decode `s` if we decode each integer in `s` as individual letters. Suppose we check if we can decode `s[1]s[2]` as a single letter. If the sum can be intepreted as a single letter, then we need to know how many ways there are to interpret the first integer `s[0]` (could be 0 or 1). Hence, there are at most `3` ways to decode `s`.

When `s` is of length `4`, we aren't adding any new ways to decode `s` if we interpret each individual digit as a letter. But if we interpret `s[2]s[3]` as a single letter, we need to know how many ways there are to intepret `s` up to index `1` (could be 0, 1, or 2).

Hence, we get the recurrence,

`# of ways to decode up to index i = # of ways to decode up to i - 1 + # of ways to decode up to i - 2`

This relation should seem familiar. It's the fibonnaci sequence, but with some extra conditions we have to check.

First, if `s[i]` is the digit `0`, `s[i]` doesn't map to a letter. So the # of ways to decode `s` at index `i` is currently `0`.

Second, if `s[i-1]s[i]` is not an integer between `10` and `26` inclusive, both digits cannot be decoded as a single letter. So we don't add any additional ways to decode `s` at index `i`.

## Complexity Analysis

## Time: O(N)

We iterate through all digits in `s` once.

## Space: O(N)

We need to remember the number of ways to decode `s` at each index. We create a dp array with the same length as `s`.

## Solutions

## Python

``` python
def numDecodings(self, s: str) -> int:
    if not s:
        return 0

    num_decode = [0 for _ in range(len(s))]

    if s[0] != "0":
        num_decode[0] = 1

    for i in range(1, len(s)):
        if s[i] != "0":
            num_decode[i] = num_decode[i - 1]

        if 10 <= int(s[i - 1 : i + 1]) <= 26:
            if i == 1:
                num_decode[i] += 1
            else:
                num_decode[i] += num_decode[i - 2]

    return num_decode[-1]
```

## Go

``` go
func numDecodings(s string) int {
    if len(s) == 0 {
        return 0
    }

    num_decode := make([]int, len(s))

    if s[0] != '0' {
        num_decode[0] = 1
    }

    for i := 1; i < len(s); i++ {
        if s[i] != '0' {
            num_decode[i] = num_decode[i - 1]
        }

        num, _ := strconv.Atoi(s[i - 1 : i + 1])
        if num >= 10 && num <= 26 {
            if i == 1 {
                num_decode[i] += 1
            } else {
                num_decode[i] += num_decode[i - 2]
            }
        }
    }

    return num_decode[len(s) - 1]
}
```

## Rust

``` rust
pub fn num_decodings(s: String) -> i32 {
    if s.len() == 0 {
        return 0;
    }

    let mut dp = vec![0; s.len()];
    let b = s.as_bytes();  // have to convert s to byte array because rust doesn't support char
                            // indexing

    if b[0] != b'0' {
        dp[0] = 1;
    }
  
    for i in 1..s.len() {
        if b[i] != b'0' {
            dp[i] = dp[i - 1];
        }

        let num = (b[i - 1] - b'0') * 10 + (b[i] - b'0');
        if num >= 10 && num <= 26 {
            if i == 1 {
                dp[i] += 1;
            } else {
                dp[i] += dp[i - 2]
            }
        }
    }

    dp[s.len() - 1]
}
```
