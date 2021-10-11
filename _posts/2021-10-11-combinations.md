---
layout: post
title: Combinations
description: 
summary: 
tags:
    - array
    - backtracking
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/combinations/)
Given two integers `n` and `k`, return *all possible combinations of `k` numbers out of the range `[1, n]`.*

You may return the answer in **any order**.

 

### Examples
**Example 1:**  
```
Input: n = 4, k = 2
Output:
[
  [2,4],
  [3,4],
  [2,3],
  [1,2],
  [1,3],
  [1,4],
]
```

**Example 2:**  
```
Input: n = 1, k = 1
Output: [[1]]
```

### Constraints
+ `1 <= n <= 20`
+ `1 <= k <= n`

## Solutions
```cpp

class Solution {
public:
    void bt(vector<vector<int>> &res,vector<int> &tmp,int i,int k,int n){
        if(tmp.size() == k){
            res.push_back(tmp); 
            return ;
        }
        for(int j=i; j<=n; j++){
            tmp.push_back(j);
            bt(res,tmp,j+1,k,n);
            tmp.pop_back();
        }
        
    }
    vector<vector<int>> combine(int n, int k) {
        vector<vector<int>> res;
        vector<int> tmp;
        bt(res,tmp,1,k,n);
        return res;
    }
   
};
```
