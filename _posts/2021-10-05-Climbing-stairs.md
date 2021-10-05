---
layout: post
title: Climbing Stairs
description: 
summary: 
tags:
    - dynamic-programming
    - leetcode
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/climbing-stairs/)
You are climbing a staircase. It takes `n` steps to reach the top.

Each time you can either climb `1` or `2` steps. In how many distinct ways can you climb to the top?

### Examples
**Example 1:**
```
Input: n = 2
Output: 2
Explanation: There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps
```

**Example 2:**
```
Input: n = 3
Output: 3
Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
```

### Constraints
+ `1 <= n <= 45`

## Solution
```cpp
class Solution {
public:
    int climbStairs(int n) {
        vector<int> mnk(n+1,1);
        for(int i=1; i<=n ; i++ ){
            int steps = 0;
            if( i-2 >= 0 )
                 steps+=mnk[i-2];
            steps+=mnk[i-1];
            mnk[i]=steps;
        }
        return mnk[n];
    }
};
```
