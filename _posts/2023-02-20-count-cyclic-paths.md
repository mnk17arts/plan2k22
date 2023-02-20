---
layout: post
title: Count Cyclic Paths
summary:
tags:
  - geeksforgeeks
  - dynamic-programming
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/aa0000a5f710ce8d41366b714341eef644ec7b82/1)

Given a triangular pyramid with its vertices marked as O, A, B and C and a number N, the task is to find the number of ways such that a person starting from the origin O initially, reaches back to the origin in N steps. In a single step, a person can go to any of its adjacent vertices.

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20200520133822/pyramid1.jpg">

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function countPaths() which takes an integer N as input parameter and returns the number of possible paths. Since the answer may be big, return it modulo (10^9+7). 


**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**

```
Input:
N = 1
Output: 0
Explanation: The minimum length of
a cyclic path is 2.
```

**Example 2:**

```
Input:
N = 2
Output: 3
Explanation: The three paths are :
O-A-O, O-B-O, O-C-O
```

### Constraints

- `1 ≤ N ≤ 1000000`

## Solutions

```cpp

class Solution{
    int MOD = 1e9+7;
public:
    int countPaths(int N){
        // code here 
        long long po = 1, pa = 0, pb = 0, pc = 0;
        for(int i = 1 ; i <= N; i++) {
            long long co = (pa + pb + pc)%MOD;
            long long ca = (po + pb + pc)%MOD;
            long long cb = (pa + po + pc)%MOD;
            long long cc = (pa + pb + po)%MOD;
            po = co, pa = ca, pb = cb, pc = cc;
        }
        return int(po);
    }
};

```
