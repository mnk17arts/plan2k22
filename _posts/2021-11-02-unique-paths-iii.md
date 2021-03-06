---
layout: post
title:  Unique Paths III
description: 
summary: 
tags:
    - array
    - backtracking
    - matrix
    - leetcode
    - cpp
    - hard
minute: 5 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/unique-paths-iii/)
You are given an `m x n` integer array `grid` where `grid[i][j]` could be:

+ `1` representing the starting square. There is exactly one starting square.
+ `2` representing the ending square. There is exactly one ending square.
+ `0` representing empty squares we can walk over.
+ `-1` representing obstacles that we cannot walk over.

Return *the number of 4-directional walks from the starting square to the ending square, that walk over every non-obstacle square exactly once.*

### Examples

**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2021/08/02/lc-unique1.jpg">
```
Input: grid = [[1,0,0,0],[0,0,0,0],[0,0,2,-1]]
Output: 2
Explanation: We have the following two paths: 
1. (0,0),(0,1),(0,2),(0,3),(1,3),(1,2),(1,1),(1,0),(2,0),(2,1),(2,2)
2. (0,0),(1,0),(2,0),(2,1),(1,1),(0,1),(0,2),(0,3),(1,3),(1,2),(2,2)
```

**Example 2:**  
<img src="https://assets.leetcode.com/uploads/2021/08/02/lc-unique2.jpg">
```
Input: grid = [[1,0,0,0],[0,0,0,0],[0,0,0,2]]
Output: 4
Explanation: We have the following four paths: 
1. (0,0),(0,1),(0,2),(0,3),(1,3),(1,2),(1,1),(1,0),(2,0),(2,1),(2,2),(2,3)
2. (0,0),(0,1),(1,1),(1,0),(2,0),(2,1),(2,2),(1,2),(0,2),(0,3),(1,3),(2,3)
3. (0,0),(1,0),(2,0),(2,1),(2,2),(1,2),(1,1),(0,1),(0,2),(0,3),(1,3),(2,3)
4. (0,0),(1,0),(2,0),(2,1),(1,1),(0,1),(0,2),(0,3),(1,3),(1,2),(2,2),(2,3)
```

**Example 3:**  
<img src="https://assets.leetcode.com/uploads/2021/08/02/lc-unique3-.jpg">
```
Input: grid = [[0,1],[2,0]]
Output: 0
Explanation: There is no path that walks over every empty square exactly once.
Note that the starting and ending square can be anywhere in the grid.
```

### Constraints
+ `m == grid.length`
+ `n == grid[i].length`
+ `1 <= m, n <= 20`
+ `1 <= m * n <= 20`
+ `-1 <= grid[i][j] <= 2`
+ There is exactly one starting cell and one ending cell.

## Solutions

```cpp
class Solution {
public:
    int res = 0, z = 1;
    void dfs(vector<vector<int>>& grid, int i, int j, int v) {
        if (i < 0 || i >= grid.size() || j < 0 || j >= grid[0].size() || grid[i][j] == -1) return;
        
        if (grid[i][j] == 2) {
            if(z == v) res++; 
            return;
        }
        
        grid[i][j] = -1;
        
        dfs(grid, i+1, j, v+1);
        dfs(grid, i-1, j, v+1);
        dfs(grid, i, j+1, v+1);
        dfs(grid, i, j-1, v+1);
        
        grid[i][j] = 0;
        
    }
    
    int uniquePathsIII(vector<vector<int>>& grid) {
        int x, y;
        for (int i = 0; i < grid.size(); i++) {
            for (int j = 0; j < grid[0].size(); j++) {
                if (grid[i][j] == 1) x = i, y = j;
                else if (grid[i][j] == 0) z++;
            }
        }
        
        dfs(grid, x, y, 0);
        return res;
    }
};

```

