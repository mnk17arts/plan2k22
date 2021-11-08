---
layout: post
title: Unique Binary Search Trees
description: 
summary:
tags:
    - dynamic-programming
    - tree 
    - binary-tree
    - leetcode
    - cpp
    - medium
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/unique-binary-search-trees/)
Given an integer `n`, return *the number of structurally unique BST's (binary search trees) which has exactly `n` nodes of unique values from `1` to `n`*.

### Examples

**Example 1:**    
<img src="https://assets.leetcode.com/uploads/2021/01/18/uniquebstn3.jpg">
```
Input: n = 3
Output: 5
```

**Example 2:**   
```
Input: n = 1
Output: 1
```

### Constraints
+ `1 <= n <= 19`

## Solutions

```cpp
class Solution {
public:
    int numTrees(int n) {
      
      if(n==1) return 1;
      
      int dp[n+1];
      for(int i=0;i<n+1;i++) dp[i]=0;
      dp[0]=dp[1]=1;
      
      for(int i=2; i<=n; i++)
        for(int j=1; j<=i; j++)
          dp[i] += dp[j-1]*dp[i-j];
      
      return dp[n];
    }
};
```

