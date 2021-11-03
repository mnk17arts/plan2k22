---
layout: post
title: Integer Break
description: 
summary: 
tags:
    - dynamic-programming
    - leetcode
    - cpp
    - medium
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/integer-break/)
Given an integer `n`, break it into the sum of `k` positive integers, where `k >= 2`, and maximize the product of those integers.

Return *the maximum product you can get.*


### Examples

**Example 1:**  
```
Input: n = 2
Output: 1
Explanation: 2 = 1 + 1, 1 × 1 = 1.
```

**Example 2:**  
```
Input: n = 10
Output: 36
Explanation: 10 = 3 + 3 + 4, 3 × 3 × 4 = 36.
```

### Constraints
+ `2 <= n <= 58`

## Solutions

```cpp
class Solution {
public:
    int integerBreak(int n) {
      int dp[n+1];
      
      dp[0] = dp[1] = dp[2] = 1;
      for(int i=3; i<n+1; i++){
        dp[i] = 0;
        for(int j=0; j<i/2; j++){
          int r = j+1;
          int l = i-r;
          dp[i] = max(dp[i], max( dp[l]*(r), (l)*(r)) );
        }
      }
      return dp[n];
    }
};
```

