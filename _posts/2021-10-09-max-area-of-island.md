---
layout: post
title: Max Area of Island
description: 
summary: 
tags:
    - DFS
    - array
    - matrix
    - BFS
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/max-area-of-island/)
You are given an `m x n` binary matrix `grid`. An island is a group of `1`'s (representing land) connected **4-directionally** (horizontal or vertical.) You may assume all four edges of the grid are surrounded by water.

The **area** of an island is the number of cells with a value `1` in the island.

Return *the maximum **area** of an island in `grid`. If there is no island, return `0`.*

### Examples
**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2021/05/01/maxarea1-grid.jpg" height="350">
```
Input: grid = [[0,0,1,0,0,0,0,1,0,0,0,0,0],[0,0,0,0,0,0,0,1,1,1,0,0,0],[0,1,1,0,1,0,0,0,0,0,0,0,0],[0,1,0,0,1,1,0,0,1,0,1,0,0],[0,1,0,0,1,1,0,0,1,1,1,0,0],[0,0,0,0,0,0,0,0,0,0,1,0,0],[0,0,0,0,0,0,0,1,1,1,0,0,0],[0,0,0,0,0,0,0,1,1,0,0,0,0]]
Output: 6
Explanation: The answer is not 11, because the island must be connected 4-directionally.
```

**Example 2:**  
```
Input: grid = [[0,0,0,0,0,0,0,0]]
Output: 0
```

### Constraints
+ `m == grid.length`
+ `n == grid[i].length`
+ `1 <= m, n <= 50`
+ `grid[i][j] is either 0 or 1`

## Solutions
```cpp
class Solution {
public:
    
    void findArea( vector<vector<int>>& grid,int i,int j,int &count){
        
        if( i<0 || j<0 || i>=grid.size() || j>=grid[0].size() || grid[i][j] == 0) return ;
        
        grid[i][j] = 0;
        count++;
        
        findArea(grid,i-1,j,count);
        findArea(grid,i,j-1,count);
        findArea(grid,i,j+1,count);
        findArea(grid,i+1,j,count);

    }
    
    int maxAreaOfIsland(vector<vector<int>>& grid) {
    
        int mx=0,count;
        
        for( int i = 0 ; i < grid.size() ; i++ )
            for( int j = 0 ; j < grid[0].size() ; j++ ){
                if(grid[i][j] == 1){
                    count = 0 ;
                    findArea(grid,i,j,count);
                    mx = max(mx,count);
                }
            }
            
        return mx;
    }
};
```
