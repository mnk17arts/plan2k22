---
layout: post
title: Unique Paths II
description: 
summary: 
tags:
    - array
    - matrix
    - dynamic-programming
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/unique-paths-ii/)
A robot is located at the top-left corner of a `m x n` grid (marked 'Start' in the diagram below).

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

Now consider if some obstacles are added to the grids. How many unique paths would there be?

An obstacle and space is marked as `1` and `0` respectively in the grid.

### Examples

**Example 1:**   
<img src="https://assets.leetcode.com/uploads/2020/11/04/robot1.jpg"> 
```
Input: obstacleGrid = [[0,0,0],[0,1,0],[0,0,0]]
Output: 2
Explanation: There is one obstacle in the middle of the 3x3 grid above.
There are two ways to reach the bottom-right corner:
1. Right -> Right -> Down -> Down
2. Down -> Down -> Right -> Right
```

**Example 2:**  
<img src="https://assets.leetcode.com/uploads/2020/11/04/robot2.jpg">
```
Input: obstacleGrid = [[0,1],[0,0]]
Output: 1
```

### Constraints
+ `m == obstacleGrid.length`
+ `n == obstacleGrid[i].length`
+ `1 <= m, n <= 100`
+ `obstacleGrid[i][j]` is `0` or `1`


## Solutions

```cpp

class Solution {
public:
    int uniquePathsWithObstacles(vector<vector<int>>& obstacleGrid) {
        
        if(obstacleGrid[0][0] == 1) return 0;    
        
        int m=obstacleGrid.size();
        int n=obstacleGrid[0].size();
        
        vector<vector<int>> dp(m,vector<int>(n,1));
        
        for(int i=0; i<m; i++)
            for(int j=0; j<n; j++){
                if(obstacleGrid[i][j] == 1)
                    dp[i][j] = 0;
                else{
                   if(i==0 && j>0) 
                        dp[i][j] = dp[i][j-1];
                    else if(j==0 && i>0) 
                        dp[i][j] = dp[i-1][j];
                    else if(i>0 && i<m && j>0 && j<n)
                        dp[i][j] = dp[i-1][j]+dp[i][j-1];                     
                }
            }
        
        return dp[m-1][n-1];
    }
};

```

