+++
title="Sum of Two Integers"
date=2020-05-12

[taxonomies]
tags = ["Binary"]
authors = ["Allan Phu"]
+++

## Problem Link

[https://leetcode.com/problems/sum-of-two-integers/](https://leetcode.com/problems/sum-of-two-integers/)

## How to solve

We xor `a` and `b` to get their sum without carries. We store the result in `a`. To find the carries, we do a bitwise `and`/`&` and leftshift by 1. We store this result in `b`. We repeat the above two steps until `b` is zero (we have no more bits to carry). Finally, we return `a`, which would then store the sum with carries.

For Python, negative integers have an infinite number of ones. For example, if we add -1 and 1, we would carry 1 an infinite number of times. So we must limit the number of carries by checking if `a` exceeds the maximum positive value of a 32-bit integer. If `a` exceeds 2^31 - 1, we have to tell Python to interpret the number as a signed integer. We can do this by using the tilde ~ operator. However in Python, the ~ operator flips all the bits. To get around this, we flip 32 bits of `a` using a mask, then invoke the ~ operator.

## Complexity Analysis

## Time: O(N)

In the worst case, we would have N - 1 carries.

## Space: O(1)

In Python, we have constant variables for the bit mask and maximum positive 32-bit integer. In Go, we only use a and b. In Rust, we use one temp variable.

## Solutions

## Python

``` python
def getSum(self, a: int, b: int) -> int:
    mask = 2**32 - 1
    max_pos_int = 2**31 - 1

    while b:
        a, b = (a ^ b) & mask, ((a & b) << 1) & mask

    if a <= max_pos_int:
        return a
    else:
        return ~(a ^ mask)
```

## Go

``` go
func getSum(a int, b int) int {
    for b != 0 {
        a, b = a ^ b, (a & b) << 1
    }
    return a
}
```

## Rust

``` rust
pub fn get_sum(a: i32, b: i32) -> i32 {
    let mut sum = a;
    let mut carry = b;
    let mut temp = 0;
    while carry != 0 {
        temp = sum ^ carry;
        carry = (sum & carry) << 1;
        sum = temp;
    }
    sum
}
```
