---
layout: post
title: Perfect Squares
description: 
summary: 
tags:
    - dynamic-programming
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/perfect-squares/)
Given an integer `n`, return *the least number of perfect square numbers that sum to `n`.*

A **perfect square** is an integer that is the square of an integer; in other words, it is the product of some integer with itself. For example, `1, 4, 9,` and `16` are perfect squares while `3` and `11` are not.

### Examples

**Example 1:**  
```
Input: n = 12
Output: 3
Explanation: 12 = 4 + 4 + 4.
```

**Example 2:**  
```
Input: n = 13
Output: 2
Explanation: 13 = 4 + 9.
```

### Constraints
+ `1 <= n <= 10^4`


## Solutions

```cpp

class Solution {
public:
    int numSquares(int n) {
        vector<int> dp(n+1,n+1);
        dp[0] = 0;
        int i=1;
        while(i*i<=n){
            for(int j=i*i; j<dp.size(); j++){
                dp[j] = min(dp[j-i*i]+1,dp[j]);
            }
            i++;
        }
        return dp[n];
    }
};

```
