---
layout: post
title: Rotting Oranges
description: 
summary: 
tags:
    - array
    - matrix
    - bfs
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/rotting-oranges/)  
You are given an `m x n` grid where each cell can have one of three values:

`0` representing an empty cell,
`1` representing a fresh orange, or
`2` representing a rotten orange.
Every minute, any fresh orange that is 4-directionally adjacent to a rotten orange becomes rotten.

Return *the minimum number of minutes that must elapse until no cell has a fresh orange. If this is impossible, return `-1`.*

### Examples
**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2019/02/16/oranges.png" height="200" >
```
Input: grid = [[2,1,1],[1,1,0],[0,1,1]]
Output: 4
```

**Example 2:**  
```
Input: grid = [[2,1,1],[0,1,1],[1,0,1]]
Output: -1
Explanation: The orange in the bottom left corner (row 2, column 0) is never rotten, because rotting only happens 4-directionally.
```

**Example 3:**  
```
Input: grid = [[0,2]]
Output: 0
Explanation: Since there are already no fresh oranges at minute 0, the answer is just 0.
```

### Constraints
+ `m == grid.length`
+ `n == grid[i].length`
+ `1 <= m, n <= 10`
+ `grid[i][j] is 0, 1, or 2`

## Solutions
```cpp
class Solution {
public:
    int xy[4][2] = {
        {1,0},{0,1},{-1,0},{0,-1}
        };
    // up,right,down,left
    
    bool check(int i,int j,int n,int m){
        return !(i<0||i>=n||j<0||j>=m);
    } // checks if the given indexes are valid
    
    int bfs(queue<vector<int>>& xym,vector<vector<int>>& grid){
        int mi=0;

        while(!xym.empty()){
            int x = xym.front()[0];
            int y = xym.front()[1];
            mi = xym.front()[2];
            xym.pop();

            for(int i=0; i<4; i++)
                if( check(x+xy[i][0],y+xy[i][1],grid.size(),grid[0].size()) && grid[x+xy[i][0]][y+xy[i][1]]==1){
                    grid[x+xy[i][0]][y+xy[i][1]] = 2;
                    xym.push({ x+xy[i][0], y+xy[i][1], mi+1});
                }
        }
        return mi;
    }
    
    int orangesRotting(vector<vector<int>>& grid) {

        queue<vector<int>> xym;
        int n=grid.size();
        int m=grid[0].size();

        for(int i=0;i<n;i++)
            for(int j=0;j<m;j++)
                if(grid[i][j]==2)
                    xym.push({i, j, 0});

        int mi = bfs(xym, grid);

        for(int i=0;i<n;i++)
            for(int j=0;j<m;j++)
                if(grid[i][j]==1)
                    return -1;

        return mi;
    }
};
```
