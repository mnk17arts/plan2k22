---
layout: post
title:  Counting Bits
summary:
tags:
    - leetcode
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/counting-bits)  

Given an integer `n`, return an array `ans` of length `n + 1` such that for each `i (0 <= i <= n)`, `ans[i]` is the number of `1`'s in the binary representation of `i`.


### Examples
**Example 1:**  
```
Input: n = 2
Output: [0,1,1]
Explanation:
0 --> 0
1 --> 1
2 --> 10
```

**Example 2:**  
```
Input: n = 5
Output: [0,1,1,2,1,2]
Explanation:
0 --> 0
1 --> 1
2 --> 10
3 --> 11
4 --> 100
5 --> 101
```

### Constraints

+ `0 <= n <= 10^5`

## Solutions

```cpp
class Solution {
public:
    int bits(int i){
      int res=0;
      while(i>0){
        i = (i & (i-1));
        res++;
      }
      return res;
    } 
    vector<int> countBits(int n) {
      vector<int> ans(n+1);
      for(int i=0; i<=n; i++){
        ans[i]=bits(i);
      }
      return ans;
    }
};
```