---
layout: post
title:  Plates Between Candles
description: 
summary: 
tags:
    - string
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/plates-between-candles/)
There is a long table with a line of plates and candles arranged on top of it. You are given a **`0`-indexed** string `s` consisting of characters `'*'` and `'|'` only, where a `'*'` represents a **plate** and a `'|'` represents a **candle**.

You are also given a **`0`-indexed** 2D integer array queries where `queries[i] = [lefti, righti]` denotes the **substring** `s[lefti...righti]` (**inclusive**). For each query, you need to find the **number** of plates **between candles** that are **in the substring**. A plate is considered **between candles** if there is at least one candle to its left **and** at least one candle to its right **in the substring**.

+ For example, `s = "||**||**|*"`, and a query `[3, 8]` denotes the substring `"*||**|"`. The number of plates between candles in this substring is `2`, as each of the two plates has at least one candle **in the substring** to its left **and** right.
Return *an integer array `answer` where `answer[i]` is the answer to the `i`th query.*


### Examples

**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2021/10/04/ex-1.png"> 
```
Input: s = "**|**|***|", queries = [[2,5],[5,9]]
Output: [2,3]
Explanation:
- queries[0] has two plates between candles.
- queries[1] has three plates between candles.
```

**Example 2:**  
<img src="https://assets.leetcode.com/uploads/2021/10/04/ex-2.png">
```
Input: s = "***|**|*****|**||**|*", queries = [[1,17],[4,5],[14,17],[5,11],[15,16]]
Output: [9,0,0,0,0]
Explanation:
- queries[0] has nine plates between candles.
- The other queries have zero plates between candles.
```

### Constraints
+ `3 <= s.length <= 10^5`
+ `s` consists of `'*'` and `'|'` characters.
+ `1 <= queries.length <= 10^5`
+ `queries[i].length == 2`
+ `0 <= lefti <= righti < s.length`


## Solutions

```cpp
class Solution {
public:
    vector<int> platesBetweenCandles(string s, vector<vector<int>>& queries) {
      int n = s.size();
      vector<int> l(n), r(n), c(n);
      vector<int> ans;
      r[n-1] = (s[n-1]=='|' ? n-1 : -1);
      for(int i=n-2; i>=0 ; i--) r[i] = (s[i]=='|' ? i : r[i+1]);
      l[0] = (s[0]=='|' ? 0 : -1);
      for(int i=1; i<n; i++) l[i] = (s[i]=='|' ? i : l[i-1]);
      c[0] = (s[0]=='|');
      for(int i=1; i<n; i++) c[i] = (s[i]=='|') + c[i-1];
      
      for(auto i: queries){
        int ls = i[0];
        int rs = i[1];
        ls = r[ls], rs = l[rs]; 
        if(ls == -1 or rs == -1 or ls > i[1] or rs < i[0] ) ans.push_back(0);
        else ans.push_back(rs - ls - c[rs] + c[ls])  ;
      }
      return ans;
    }
};
```

