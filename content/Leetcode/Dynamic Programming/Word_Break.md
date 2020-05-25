+++
title="Word Break"
date=2020-05-18

[taxonomies]
tags = ["Dynamic Programming"]
authors = ["Allan Phu"]
+++

## Problem Link

[https://leetcode.com/problems/word-break/](https://leetcode.com/problems/word-break/)

## How to solve

Create a hashset containing the words in `wordDict`. Create a dp array of length `s` + 1. dp[i] is true if the substring in `s` ending at index `i-1` is a dictionary word. Hence, the zero index of `dp` represents the empty string, which is trivially a word in `wordDict`. We iterate through the dp array, checking if index i is the end of a dictionary word (i.e. if dp[i] is true). If so, we iterate through the possible substrings from i to len(s) and check if those are dictionary words.

## Complexity Analysis

## Time: O(N)

In the worst case, every other character of string `s` is a dictionary word.

## Space: O(max(M,N))

Let N be the length of string `s`, and M the number of words in `wordDict`. We keep an array of size length `s` + 1 to keep track of words found. We also create a hashset of words in `wordDict`.

## Solutions

## Python

``` python
def wordBreak(self, s: str, wordDict: List[str]) -> bool:
    words = set(wordDict)
    dp = [False for _ in range(len(s))]
    dp[0] = True
    for i in range(len(s)):
        if dp[i]:
            for j in range(i, len(s)):
                if s[i:j+1] in words:
                    dp[j+1] = True
    return dp[-1]
```

## Go

``` go
func wordBreak(s string, wordDict []string) bool {
    words := make(map[string]bool)
    for _, word := range wordDict {
        words[word] = true
    }

    dp := make([]bool, len(s) + 1)
    dp[0] = true

    for i := range s {
        if dp[i] == true {
            for j := i; j < len(s); j++ {
                if _, ok := words[s[i : j + 1]]; ok {
                    dp[j + 1] = true
                }  
            }
        }
    }

    return dp[len(s)]
}
```

## Rust

``` rust
use std::collections::HashSet;

impl Solution {
    pub fn word_break(s: String, word_dict: Vec<String>) -> bool {
        let mut words = HashSet::with_capacity(word_dict.len());
        for word in &word_dict {
            words.insert(word);
        }

        let mut dp = vec![false; s.len() + 1];
        dp[0] = true;

        for i in 0..s.len() {
            if dp[i] {
                for j in i..s.len() {
                    if words.contains(&String::from(&s[i..j+1])) {
                        dp[j + 1] = true;
                    }
                }
            }
        }

        dp[s.len()]
    }
}
```
