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

This problem can be solved recursively or iteratively (for now, the solutions posted below are iterative).

To perform a deep clone of a graph, we must do two things:

1. Create a deep clone (i.e. allocate memory for a Node on the heap) for each of the nodes in the input graph
2. For each cloned node, ensure that it has the same neighbors as in the input graph.

 First, clone the input `node`. Create a hashmap (called `visited`) that maps the nodes in the input graph to their cloned counterparts. Map the input `node` to the cloned node. Next, create a stack/queue and append to it input node. We will use the stack/queue to keep track of which nodes that still need their neighbor list populated.

 While the stack/queue is not empty, perform the following steps:

1. Pop/Deque the node from stack/queue
2. For each neighbor of node:
3. Check if neighbor has been cloned
    1. If so, append cloned neighbor to list of neighbors for the cloned node
    2. Else, create a clone of neighbor and add a pair (neighbor, cloned neighbor) to the hashmap. Then append the cloned neighbor to the list of neighbors for the cloned node
4. Return the cloned input node.

## Complexity Analysis

## Time: O(|V| + |E|)

We clone every node in the original input graph. For every node, we check all of it's neighbors and append the cloned neighbors to the cloned node's neighbor list.

## Space: O(|V|)

For depth-first-search or breadth-first-search, we maintain a stack or heap that holds the unprocessed nodes in the input graph. In the worst case, a node might be connected to every other node (i.e. have `|V| - 1` neighbors).

## Solutions

## Python

``` python
def cloneGraph(self, node: 'Node') -> 'Node':
    # DFS solution
    if not node:
        return None

    new_node = Node(node.val)
    visited = {node: new_node}

    stack = [node]

    while stack:
        old_node = stack.pop()

        for neighbor in old_node.neighbors:
            if neighbor not in visited:
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
    visited = {node: new_node}

    queue = deque([node])

    while queue:
        old_node = queue.popleft()

        for neighbor in old_node.neighbors:
            if neighbor not in visited:
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
        return nil
    }

    new_node := &Node{Val: node.Val}

    visited := make(map[*Node]*Node)
    visited[node] = new_node

    stack := []*Node{node}

    for len(stack) > 0 {
        old_node := stack[len(stack) - 1]
        stack = stack[:len(stack) - 1]

        for _, neighbor := range old_node.Neighbors {
            if _, exists := visited[neighbor]; !exists {
                visited[neighbor] = &Node{Val: neighbor.Val}
                stack = append(stack, neighbor)
            }
            visited[old_node].Neighbors = append(visited[old_node].Neighbors, visited[neighbor])
        }
    }

    return new_node
}
```

``` go
func cloneGraph(node *Node) *Node {
    // BFS Solution
    if node == nil {
        return nil
    }

    new_node := &Node{Val: node.Val}

    visited := make(map[*Node]*Node)
    visited[node] = new_node

    queue := []*Node{node}

    for len(queue) > 0 {
        old_node := queue[0]
        queue = queue[1:]

        for _, neighbor := range old_node.Neighbors {
            if _, exists := visited[neighbor]; !exists {
                visited[neighbor] = &Node{Val: neighbor.Val}
                queue = append(queue, neighbor)
            }
            visited[old_node].Neighbors = append(visited[old_node].Neighbors,                                                              visited[neighbor])
        }
    }

    return new_node
}
```

## Rust

``` rust
No Rust option on Leetcode :(
```
