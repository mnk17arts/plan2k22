---
layout: post
title: As Far from Land as Possible 
summary:
tags:
    - leetcode
    - array
    - dynamic-programming
    - bfs
    - matrix
    - cpp
    - medium
minute: 15+ min
---

## Problem Statement - [*link*](https://leetcode.com/problems/as-far-from-land-as-possible/description/)  

Given an n x n grid containing only values 0 and 1, where 0 represents water and 1 represents land, find a water cell such that its distance to the nearest land cell is maximized, and return the distance. If no land or water exists in the grid, return -1.

The distance used in this problem is the Manhattan distance: the distance between two cells (x0, y0) and (x1, y1) is |x0 - x1| + |y0 - y1|.

### Examples


**Example 1:**   
<img src="https://assets.leetcode.com/uploads/2019/05/03/1336_ex1.JPG">

```
Input: grid = [[1,0,1],[0,0,0],[1,0,1]]
Output: 2
Explanation: The cell (1, 1) is as far as possible from all the land with distance 2.
```

**Example 2:**   
<img src="https://assets.leetcode.com/uploads/2019/05/03/1336_ex2.JPG">
```
Input: grid = [[1,0,0],[0,0,0],[0,0,0]]
Output: 4
Explanation: The cell (2, 2) is as far as possible from all the land with distance 4.
```


### Constraints

+ `n == grid.length`
+ `n == grid[i].length`
+ `1 <= n <= 100`
+ `grid[i][j]` is `0` or `1`

## Solutions

```cpp

class Solution {
public:
    int maxDistance(vector<vector<int>>& grid) {
        int maxDis = -1;
        int n = grid.size();
        int d[5] = { 0, -1, 0, 1, 0};
        queue<pair<int, int>> q;
        for(int i = 0; i < n; i++) {
            for(int j = 0; j < n; j++) {
                if(grid[i][j] == 1) {
                    q.push({i, j});
                }
            }
        }
        if(q.size() == n*n) {
            return maxDis;
        }
        while(q.size()) {
            int s = q.size();
            while(s--){
                int x = q.front().first;
                int y = q.front().second;
                q.pop();
                for(int k = 0; k < 4; k++) {
                    int i = x + d[k];
                    int j = y + d[k + 1];
                    if(i < 0 || n <= i || j < 0 || n <= j) {
                        continue;
                    }
                    if(grid[i][j] == 0) {
                        q.push({i, j});
                        grid[i][j] = 1;
                    }
                }                
            }
            maxDis++;
        }
        return maxDis;
    }
};

```

