---
layout: post
title: N-th Tribonacci Number                       
summary:
tags:
    - leetcode
    - dynamic-programming
    - cpp
    - easy
minute: 5+ min
---

## Problem Statement - [*link*](https://leetcode.com/problems/n-th-tribonacci-number/description/)  

The Tribonacci sequence Tn is defined as follows: 

T0 = 0, T1 = 1, T2 = 1, and Tn+3 = Tn + Tn+1 + Tn+2 for n >= 0.

Given n, return the value of Tn.

### Examples


**Example 1:**   
```
Input: n = 4
Output: 4
Explanation:
T_3 = 0 + 1 + 1 = 2
T_4 = 1 + 1 + 2 = 4
```

**Example 2:**   
```
Input: n = 25
Output: 1389537
```



### Constraints

+ `0 <= n <= 37`
+ The answer is guaranteed to fit within a 32-bit integer, ie. a`nswer <= 2^31 - 1`.

## Solutions

```cpp
class Solution {
public:
    int tribonacci(int n) {
        if(n==0) return 0;
        if(n<3) return 1;
        int dp[n+1] ;
        dp[0]=0,dp[1]=1,dp[2]=1;
        for(int i=3;i<=n;i++)
            dp[i]=dp[i-1]+dp[i-2]+dp[i-3];
        return dp[n];
    }
};
```

