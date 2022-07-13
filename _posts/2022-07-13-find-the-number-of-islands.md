---
layout: post
title: Find the number of islands                 
summary:
tags:
    - dfs
    - graph
    - geeksforgeeks
    - cpp
    - medium
minute: 11 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/find-the-number-of-islands/0/?track=DSASP-Graph&batchId=154#)  

Given a grid of size `n*m` (`n` is the number of rows and `m` is the number of columns in the grid) consisting of '`0`'s (Water) and '`1`'s(Land). Find the number of islands.

Note: An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically or diagonally i.e., in all `8` directions.

**Your Task:** 
You don't need to read or print anything. Your task is to complete the function numIslands() which takes the grid as an input parameter and returns the total number of islands.


**Expected Time Complexity:** `O(n*m)`           
**Expected Auxiliary Space:** `O(n*m)`


### Examples

**Example 1:**   
```
Input:
grid = [[0,1,1,1,0,0,0],[0,0,1,1,0,1,0]]
Output:
2
Expanation:
The grid is-
0 1 1 1 0 0 0
0 0 1 1 0 1 0 
There are two islands in the grid.
``` 


### Constraints

+ `1 ≤ n, m ≤ 500`

## Solutions

```cpp
class Solution
{
    public:
    void bfs(vector<vector<char>>& grid,int n,int m,int r,int c) {
        queue<pair<int,int>> q;
        q.push({n,m});
        while(!q.empty())  {
            auto it=q.front();
            q.pop();
            int i=it.first;
            int j=it.second;
            grid[i][j]='0';
            if(i+1 < r && grid[i+1][j]=='1' )    {
                q.push({i+1,j});
                grid[i+1][j]='0';
            }
            if(j+1 < c && grid[i][j+1]=='1')    {
                q.push({i,j+1});
                 grid[i][j+1]='0';
            }
            if(i-1 >=0 && grid[i-1][j]=='1')    {
                q.push({i-1,j});
                 grid[i-1][j]='0';
            }
            if(j-1 >=0 && grid[i][j-1]=='1')    {
                q.push({i,j-1});
                 grid[i][j-1]='0';
            }
            if(i+1 < r && j+1 < c && grid[i+1][j+1]=='1')    {
                q.push({i+1,j+1});
                 grid[i+1][j+1]='0';
            }
            if(i+1 < r && j-1 >= 0 && grid[i+1][j-1]=='1')     {
                q.push({i+1,j-1});
                 grid[i+1][j-1]='0';
            }
            if(i-1 >=0 && j+1 < c && grid[i-1][j+1]=='1')    {
                q.push({i-1,j+1});
                 grid[i-1][j+1]='0';
            }
            if(i-1 >= 0 && j-1 >= 0 && grid[i-1][j-1]=='1' )    {
                q.push({i-1,j-1});
                 grid[i-1][j-1]='0';
            }
        }
    }
    // Function to find the number of islands.
    int numIslands(vector<vector<char>>& grid) {
        // Code here
        int n=grid.size();
        int m=grid[0].size();
        int res=0;
      
        for(int i=0;i<n;i++) {
            for(int j=0;j<m;j++) {
                if(grid[i][j]=='1') {
                    res++;
                    bfs(grid,i,j,n,m);
                }
            }
        }
        return res;
    }
};
```

