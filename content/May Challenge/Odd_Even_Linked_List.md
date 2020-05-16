+++
title="Odd Even Linked List"
date=2020-05-16
+++

## Problem Link

[https://leetcode.com/problems/odd-even-linked-list/](https://leetcode.com/problems/odd-even-linked-list/)

## How to solve

## Complexity Analysis

## Time: O(N)

## Space: O(1)

## Solutions

## Python

``` python
def oddEvenList(self, head: ListNode) -> ListNode:
    if not head:
        return head

    odd = head
    first_even = head.next
    even = first_even

    while even and even.next:
        odd.next = even.next
        odd = odd.next
        even.next = odd.next
        even = even.next

    odd.next = first_even

    return head
```

## Go

``` go
func oddEvenList(head *ListNode) *ListNode {
    if head == nil {
        return head
    }

    odd := head
    first_even := head.Next
    even := first_even

    for even != nil && even.Next != nil {
        odd.Next = even.Next
        odd = odd.Next
        even.Next = odd.Next
        even = even.Next
    }

    odd.Next = first_even

    return head
}
```

## Rust

``` rust

```
