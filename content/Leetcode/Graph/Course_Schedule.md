+++
title="Course Schedule"
date=2020-05-26

[taxonomies]
tags = ["Graph"]
authors = ["Allan Phu"]
+++

## Problem Link

[https://leetcode.com/problems/course-schedule/](https://leetcode.com/problems/course-schedule/)

## How to solve

## Complexity Analysis

## Time

## Space

## Solutions

## Python

``` python
def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
    adj_list = [[] for _ in range(numCourses)]
    for preq in prerequisites:
        adj_list[preq[0]].append(preq[1])

    visiting = set()
    visited = set()

    def has_cycle(course):
        if course in visiting:
            return True
        if course in visited:
            return False

        visiting.add(course)

        for preq_class in adj_list[course]:
            if has_cycle(preq_class):
                return True

        visiting.remove(course)
        visited.add(course)
        return False

    for i in range(numCourses):
        if has_cycle(i):
            return False

    return True
```

## Go

``` go
func canFinish(numCourses int, prerequisites [][]int) bool {
    adj_list := make([][]int, numCourses)
    for i := range adj_list {
        adj_list[i] = make([]int, 0)
    }

    for i := range prerequisites {
        preq := prerequisites[i][0]
        class := prerequisites[i][1]
        adj_list[preq] = append(adj_list[preq], class)
    }

    visiting := make(map[int]bool)
    visited := make(map[int]bool)

    for i := 0; i < numCourses; i++ {
        if hasCycle(i, adj_list, visiting, visited) {
            return false
        }
    }

    return true
}

func hasCycle(course int, adj_list [][]int, visiting map[int]bool, visited map[int]bool) bool {
    if _, ok := visiting[course]; ok {
        return true
    } else if _, ok := visited[course]; ok {
        return false
    }

    visiting[course] = true

    for i := range adj_list[course] {
        if hasCycle(adj_list[course][i], adj_list, visiting, visited) {
            return false
        }
    }

    delete(visiting, course)
    visited[course] = true
    return false
}
```

## Rust

``` rust
use std::collections::HashSet;

impl Solution {
    pub fn can_finish(num_courses: i32, prerequisites: Vec<Vec<i32>>) -> bool {

        let num_courses = num_courses as usize;
        let mut adj_list: Vec<Vec<i32>> = vec![Vec::new(); num_courses];
        for preq in &prerequisites {
            adj_list[preq[0] as usize].push(preq[1]);
        }

        let mut visiting = HashSet::new();
        let mut visited = HashSet::new();

        for i in 0..num_courses {
            if has_cycle(i as i32, &adj_list, &mut visiting, &mut visited) {
                return false;
            }
        }

        true
    }
}

pub fn has_cycle(course: i32, 
                 adj_list: &Vec<Vec<i32>>, 
                 mut visiting: &mut HashSet<i32>, 
                 mut visited: &mut HashSet<i32>) -> bool {

    if visiting.contains(&course) {
        return true;
    }
    if visited.contains(&course) {
        return false;
    }

    visiting.insert(course);

    for i in 0..adj_list[course as usize].len() {
        if has_cycle(adj_list[course as usize][i], 
                     &adj_list, 
                     &mut visiting, 
                     &mut visited) {
            return true;
        }
    }

    visiting.remove(&course);
    visited.insert(course);
    false
}
```
