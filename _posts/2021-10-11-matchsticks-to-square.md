---
layout: post
title: Matchsticks to Square
description: 
summary: 
tags:
    - array
    - backtracking
    - bit-manipulation
    - bitmasks
    - dynamic-programming
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/matchsticks-to-square/)
You are given an integer array matchsticks where `matchsticks[i]` is the length of the `ith` matchstick. You want to use **all the matchsticks** to make one square. You **should not break** any stick, but you can link them up, and each matchstick must be used **exactly one time**.

Return *`true` if you can make this square and `false` otherwise.*

 

### Examples
**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2021/04/09/matchsticks1-grid.jpg" height="300" >
```
Input: matchsticks = [1,1,2,2,2]
Output: true
Explanation: You can form a square with length 2, one side of the square came two sticks with length 1.
```

**Example 2:**  
```
Input: matchsticks = [3,3,3,3,4]
Output: false
Explanation: You cannot find a way to form a square with all the matchsticks.
```

### Constraints
+ `1 <= matchsticks.length <= 15`
+ `1 <= matchsticks[i] <= 10^8`

## Solutions
```cpp

class Solution {
public:

    bool bt(vector<int>& ms,vector<bool>& vis,int s,int sum,int pos,int c){

        if(c == 0) return true;

        if(sum == s) 
            return bt(ms,vis,s,0,0,c-1);

        for(int i=pos; i<ms.size(); i++){

            if( vis[i] || sum+ms[i]> s) continue;

            vis[i] = true;

            if (bt(ms,vis,s,sum+ms[i],i+1,c)) return true;
            
            vis[i] = false;
        }

        return false;
    }

    bool makesquare(vector<int>& ms) {

        int per = 0; // perimeter
            for(auto i:ms)
                per+=i;
        
        if(per%4!=0 || ms.size()<4) return false;
        
        int side = per/4;
        vector<bool> vis(ms.size(),false);
        return bt(ms,vis,side,0,0,4); //matchsticks,visited,side,current sum,position,sides to be filled
    }
};

```
