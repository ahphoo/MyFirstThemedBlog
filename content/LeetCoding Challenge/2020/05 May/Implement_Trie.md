+++
title="Implement Trie"
date=2020-05-14
+++

## Problem Link

[https://leetcode.com/problems/implement-trie-prefix-tree/](https://leetcode.com/problems/implement-trie-prefix-tree/)

## How to solve

## Complexity Analysis

## Time

## Space

## Solutions

## Python

``` python
class TrieNode:
    def __init__(self):
        self.letters = {}
        self.isWord = False

class Trie:

    def __init__(self):
        self.root = TrieNode()

    def insert(self, word: str) -> None:
        node = self.root
        for ch in word:
            if ch in node.letters:
                node = node.letters[ch]
            else:
                node.letters[ch] = TrieNode()
                node = node.letters[ch]
        node.isWord = True

    def searchPrefix(self, prefix: str) -> TrieNode:
        node = self.root
        for ch in prefix:
            if ch in node.letters:
                node = node.letters[ch]
            else:
                return None
        return node

    def search(self, word: str) -> bool:
        node = self.searchPrefix(word)
        if node and node.isWord:
            return True
        return False

    def startsWith(self, prefix: str) -> bool:
        node = self.searchPrefix(prefix)
        if node:
            return True
        return False
```

## Go

``` go

```

## Rust

``` rust

```
