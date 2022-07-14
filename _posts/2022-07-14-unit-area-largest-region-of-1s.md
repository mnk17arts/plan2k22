---
layout: post
title: Unit Area of largest region of 1's                   
summary:
tags:
    - graph
    - dfs
    - bfs
    - geeksforgeeks
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/length-of-largest-region-of-1s-1587115620/0/?track=DSASP-Graph#)  

Given a grid of dimension `n`x`m` containing `0`s and `1`s. Find the unit area of the largest region of 1s.
Region of `1`'s is a group of `1`'s connected `8`-directionally (horizontally, vertically, diagonally).

**Your Task:** 
You don't need to read or print anyhting. Your task is to complete the function `findMaxArea()` which takes grid as input parameter and returns the area of the largest region of `1`'s.


**Expected Time Complexity:** `O(n*m)`           
**Expected Auxiliary Space:** `O(n*m)`


### Examples

**Example 1:**   
```
Input: grid = {{1,1,1,0},{0,0,1,0},{0,0,0,1}}
Output: 5
Explanation: The grid is-
1 1 1 0
0 0 1 0
0 0 0 1
```

**Example 2:**   
```
Input: grid = {{0,1}}
Output: 1
Explanation: The grid is-
0 1
The largest region of 1's is colored in 
orange.
```

### Constraints

+ `1 ≤ n, m ≤ 500`

## Solutions

```cpp
class Solution
{
    public:
    int xy[9] = {-1,0,1,0,-1,-1,1,1,-1};
    int m,n;
    int dfs(vector<vector<int>>& grid,int i,int j){
        if(i<0||i==m||j<0||j==n||grid[i][j]==0) return 0;
        grid[i][j]=0;
        int sum = 0;
        for(int a=0;a<8;a++)
            sum += dfs(grid,i+xy[a],j+xy[a+1]);
        return 1 + sum;
    }
    //Function to find unit area of the largest region of 1s.
    int findMaxArea(vector<vector<int>>& grid) {
        // Code here
        m = grid.size(), n = grid[0].size();
        int res = INT_MIN;
        for(int i=0;i<m;i++)
            for(int j=0;j<n;j++)
                if(grid[i][j])
                    res = max(res,dfs(grid,i,j));
        return res;
    }
};
```

