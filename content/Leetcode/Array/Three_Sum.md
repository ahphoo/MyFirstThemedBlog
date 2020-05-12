+++
title="3Sum"
date=2020-05-11
+++

## Problem Link

[https://leetcode.com/problems/3sum](https://leetcode.com/problems/3sum)

## How to solve

## Complexity Analysis

## Time: O(log N)

## Space: O(1)

## Solutions

## Python

``` python
def threeSum(self, nums: List[int]) -> List[List[int]]:
    nums.sort()
    ans = []

    for i in range(len(nums) - 2):
        if nums[i] > 0:
            return ans
        if i > 0 and nums[i - 1] == nums[i]:
            continue

        l = i + 1
        r = len(nums) - 1

        while l < r:
            sum_triple = nums[i] + nums[l] + nums[r]

            if sum_triple > 0:
                r -= 1
            elif sum_triple < 0:
                l += 1
            else:
                ans.append([nums[i], nums[l], nums[r]])
                while l < r and nums[l] == nums[l + 1]:
                    l += 1
                while l < r and nums[r - 1] == nums[r]:
                    r -= 1
                l += 1
                r -= 1

    return ans
```

## Go

``` go
import "sort"

func threeSum(nums []int) [][]int {
    sort.Ints(nums)
    ans := make([][]int, 0)

    for i := 0; i < len(nums) - 2; i++ {
        if nums[i] > 0 {
            return ans
        } else if (i > 0) && (nums[i - 1] == nums[i]) {
            continue
        }

        l := i + 1
        r := len(nums) - 1

        for l < r {
            sum_triple := nums[i] + nums[l] + nums[r]

            if sum_triple < 0 {
                l += 1
            } else if sum_triple > 0 {
                r -= 1
            } else {
                ans = append(ans, []int{nums[i], nums[l], nums[r]})

                for (l < r) && (nums[l] == nums[l + 1]) {
                    l += 1
                }
                for (l < r) && (nums[r] == nums[r - 1]) {
                    r -= 1
                }
                l += 1
                r -= 1
            }
        }
    }
    return ans
```

## Rust

``` rust
    pub fn three_sum(mut nums: Vec<i32>) -> Vec<Vec<i32>> {
        if nums.len() < 3 {
            return Vec::<Vec<i32>>::new();
        }
        nums.sort();
        let mut ans: Vec<Vec<i32>> = Vec::new();

        for i in 0..nums.len() - 2 {
            if nums[i] > 0 {
                return ans;
            } else if (i > 0) && (nums[i - 1] == nums[i]) {
                continue;
            }

            let mut l = i + 1;
            let mut r = nums.len() - 1;

            while l < r {
                let mut sum_triple = nums[i] + nums[l] + nums[r];

                if sum_triple < 0 {
                    l += 1;
                } else if sum_triple > 0 {
                    r -= 1;
                } else {
                    ans.push(vec![nums[i], nums[l], nums[r]]);

                    while (l < r) && (nums[l] == nums[l + 1]) {
                        l += 1;
                    }
                    while (l < r) && (nums[r] == nums[r - 1]) {
                        r -= 1;
                    }
                    l += 1;
                    r -= 1;
                }
            }
       }
        ans
    }
}
```
