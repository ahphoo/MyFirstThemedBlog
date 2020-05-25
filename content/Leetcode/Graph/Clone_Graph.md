+++
title="Clone Graph"
date=2020-05-25

[taxonomies]
tags = ["Graph"]
authors = ["Allan Phu"]
+++

## Problem Link

[https://leetcode.com/problems/clone-graph/](https://leetcode.com/problems/clone-graph/)

## How to solve

## Complexity Analysis

## Time

## Space

## Solutions

## Python

``` python
def cloneGraph(self, node: 'Node') -> 'Node':
    # DFS solution
    if not node:
        return None

    new_node = Node(node.val)
    visited = {}
    visited[node] = new_node

    stack = [node]

    while stack:
        old_node = stack.pop()

        for neighbor in old_node.neighbors:
            if neighbor in visited:
                visited[old_node].neighbors.append(visited[neighbor])
            else:
                visited[neighbor] = Node(neighbor.val)
                stack.append(neighbor)
                visited[old_node].neighbors.append(visited[neighbor])

    return new_node
```

``` python
def cloneGraph(self, node: 'Node') -> 'Node':
    # BFS solution
    if not node:
        return None

    new_node = Node(node.val)
    visited = {}
    visited[node] = new_node

    queue = deque([node])

    while queue:
        old_node = queue.popleft()

        for neighbor in old_node.neighbors:
            if neighbor in visited:
                visited[old_node].neighbors.append(visited[neighbor])
            else:
                visited[neighbor] = Node(neighbor.val)
                queue.append(neighbor)
                visited[old_node].neighbors.append(visited[neighbor])

    return new_node
```

## Go

``` go

```

## Rust

``` rust

```
