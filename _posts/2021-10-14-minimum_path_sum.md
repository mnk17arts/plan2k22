---
layout: post
title: Minimum Path Sum
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

## Problem Statement - [*link*](https://leetcode.com/problems/minimum-path-sum/)
Given a `m x n` grid filled with non-negative numbers, find a path from top left to bottom right, which minimizes the sum of all numbers along its path.

**Note:** You can only move either down or right at any point in time.

### Examples

**Example 1:**   
<img src="https://assets.leetcode.com/uploads/2020/11/05/minpath.jpg"> 
```
Input: grid = [[1,3,1],[1,5,1],[4,2,1]]
Output: 7
Explanation: Because the path 1 → 3 → 1 → 1 → 1 minimizes the sum.
```

**Example 2:**  
```
Input: grid = [[1,2,3],[4,5,6]]
Output: 12
```

### Constraints
+ `m == grid.length`
+ `n == grid[i].length`
+ `1 <= m, n <= 200`
+ `0 <= grid[i][j] <= 100`


## Solutions

```cpp

class Solution {
public:
    int minPathSum(vector<vector<int>>& grid) {

        int m = grid.size();
        int n = grid[0].size();
        
        for(int i=0; i<m; i++){
            for(int j=0; j<n; j++){
                if(i==0 and j>0)
                    grid[i][j]+=grid[i][j-1];
                else if(j==0 and i>0)
                    grid[i][j]+=grid[i-1][j];
                else if(i>0 && j>0)
                    grid[i][j] += min(grid[i-1][j],grid[i][j-1]);
            }
        }
        return grid[m-1][n-1];
    }
};

```

