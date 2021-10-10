---
layout: post
title: Number of Islands
description: 
summary: 
tags:
    - array
    - matrix
    - dfs
    - bfs
    - leetcode
    - cpp
    - medium
minute: 5 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/number-of-islands/)
Given an `m x n` 2D binary grid `grid` which represents a map of '`1`'s (land) and '`0`'s (water), return *the number of islands.*

An **island** is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

### Examples
**Example 1:**  
```
Input: grid = [
  ["1","1","1","1","0"],
  ["1","1","0","1","0"],
  ["1","1","0","0","0"],
  ["0","0","0","0","0"]
]
Output: 1
```

**Example 2:**  
```
Input: grid = [
  ["1","1","0","0","0"],
  ["1","1","0","0","0"],
  ["0","0","1","0","0"],
  ["0","0","0","1","1"]
]
Output: 3
```

### Constraints
+ `m == grid.length`
+ `n == grid[i].length`
+ `1 <= m, n <= 300`
+ `grid[i][j] is '0' or '1'`

## Solutions
```cpp
class Solution {
public:
        
    void findArea( vector<vector<char>>& grid,int i,int j){
        
        if( i<0 || j<0 || i>=grid.size() || j>=grid[0].size() || grid[i][j] == '0') return ;
        
        grid[i][j] = '0';
        findArea(grid,i-1,j);
        findArea(grid,i,j-1);
        findArea(grid,i,j+1);
        findArea(grid,i+1,j);
    }
    
    int numIslands(vector<vector<char>>& grid) {
        int ans=0;
        
        for( int i = 0 ; i < grid.size() ; i++ )
            for( int j = 0 ; j < grid[0].size() ; j++ )
                if(grid[i][j] == '1'){
                    findArea(grid,i,j);
                    ans++;
                }
            
        return ans;
    }
};
```
