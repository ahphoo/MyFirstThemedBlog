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
func cloneGraph(node *Node) *Node {
    //DFS Solution
    if node == nil {
        return nil;
    }

    new_node := new(Node)
    new_node.Val = node.Val
    new_node.Neighbors = make([]*Node, 0)

    visited := make(map[*Node]*Node)
    visited[node] = new_node

    stack := make([]*Node, 0)
    stack = append(stack, node)

    for len(stack) > 0 {
        old_node := stack[len(stack) - 1]
        stack = stack[:len(stack) - 1]

        for _, neighbor := range old_node.Neighbors {
            if _, exists := visited[neighbor]; exists {
                visited[old_node].Neighbors = append(visited[old_node].Neighbors, visited[neighbor])
            } else {
                visited[neighbor] = new(Node)
                visited[neighbor].Val = neighbor.Val
                visited[neighbor].Neighbors = make([]*Node, 0)
                visited[old_node].Neighbors = append(visited[old_node].Neighbors, visited[neighbor])
                stack = append(stack, neighbor)
            }
        }
    }

    return new_node
}
```

``` go
func cloneGraph(node *Node) *Node {
    // BFS Solution
    if node == nil {
        return nil;
    }

    new_node := new(Node)
    new_node.Val = node.Val
    new_node.Neighbors = make([]*Node, 0)

    visited := make(map[*Node]*Node)
    visited[node] = new_node

    queue := make([]*Node, 0)
    queue = append(queue, node)

    for len(queue) > 0 {
        old_node := queue[0]
        queue = queue[1:]

        for _, neighbor := range old_node.Neighbors {
            if _, exists := visited[neighbor]; exists {
                visited[old_node].Neighbors = append(visited[old_node].Neighbors, visited[neighbor])
            } else {
                visited[neighbor] = new(Node)
                visited[neighbor].Val = neighbor.Val
                visited[neighbor].Neighbors = make([]*Node, 0)
                visited[old_node].Neighbors = append(visited[old_node].Neighbors, visited[neighbor])
                queue = append(queue, neighbor)
            }
        }
    }

    return new_node
}
```

## Rust

``` rust

```
