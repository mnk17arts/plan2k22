---
layout: post
title: Shift 2D Grid
summary:
tags:
    - array
    - matrix
    - leetcode
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/shift-2d-grid)  

Given a 2D `grid` of size `m x n` and an integer `k`. You need to shift the `grid` `k` times.

In one shift operation:

+ Element at grid[i][j] moves to grid[i][j + 1].
+ Element at grid[i][n - 1] moves to grid[i + 1][0].
+ Element at grid[m - 1][n - 1] moves to grid[0][0].

Return *the 2D `grid` after applying shift operation `k` times.*

### Examples

**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2019/11/05/e1.png"> 
```
Input: grid = [[1,2,3],[4,5,6],[7,8,9]], k = 1
Output: [[9,1,2],[3,4,5],[6,7,8]]
```

**Example 2:**  
<img src="https://assets.leetcode.com/uploads/2019/11/05/e2.png"> 
```
Input: grid = [[3,8,1,9],[19,7,2,5],[4,6,11,10],[12,0,21,13]], k = 4
Output: [[12,0,21,13],[3,8,1,9],[19,7,2,5],[4,6,11,10]]
```

**Example 3:**  
```
Input: grid = [[1,2,3],[4,5,6],[7,8,9]], k = 9
Output: [[1,2,3],[4,5,6],[7,8,9]]
```

### Constraints
+ `m == grid.length`
+ `n == grid[i].length`
+ `1 <= m <= 50`
+ `1 <= n <= 50`
+ `-1000 <= grid[i][j] <= 1000`
+ `0 <= k <= 100`

## Solutions

```cpp
class Solution {
public:
    vector<vector<int>> shiftGrid(vector<vector<int>>& grid, int k) {
      int r = grid.size(), c = grid[0].size();
      vector<vector<int>> res(r, vector<int>(c));
      for(int i = 0; i<r; i++){
        for(int j = 0; j<c; j++){
          int j2 = (j + k)%(c);
          int i2 = i + (j + k)/(c);
          i2 = i2%r;
          res[i2][j2] = grid[i][j];
        }
      }
      return res;
    }
};
```

