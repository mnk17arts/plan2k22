---
layout: post
title:  Shortest Path in Binary Matrix
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

## Problem Statement - [*link*](https://leetcode.com/problems/shortest-path-in-binary-matrix/)  
Given an `n x n` binary matrix grid, return the length of the shortest **clear path** in the matrix. If there is no **clear path**, return `-1`.

A **clear path** in a binary matrix is a path from the **top-left** cell (i.e., (`0, 0`)) to the **bottom-right** cell (i.e., (`n - 1, n - 1`)) such that:

+ All the visited cells of the path are `0`.
+ All the adjacent cells of the path are **8-directionally** connected (i.e., they are different and they share an edge or a corner).

The **length of a clear path** is the number of visited cells of this path.
 
### Examples   
**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2021/02/18/example1_1.png">
```
Input: grid = [[0,1],[1,0]]
Output: 2
```

**Example 2:**   
<img src="https://assets.leetcode.com/uploads/2021/02/18/example2_1.png">
``` 
Input: board = [["X"]]
Output: [["X"]]
```

**Example 3:**   
``` 
Input: grid = [[1,0,0],[1,1,0],[1,1,0]]
Output: -1
```

### Constraints
+ `n == grid.length`
+ `n == grid[i].length`
+ `1 <= n <= 100`
+ `grid[i][j] is 0 or 1`


## Solutions

```cpp
class Solution {
public:
    
    int xy[8][2] = {{1,1}, {0,1}, {1,0}, {-1,-1}, {0,-1}, {-1,1}, {-1,0}, {1,-1}};
    int shortestPathBinaryMatrix(vector<vector<int>>& grid) {
        int s=grid.size();
        if(grid[0][0] or grid[s-1][s-1]) return -1;
        queue<vector<int>> q;
        q.push({0,0,1});
        while(!q.empty()){
            auto p = q.front();
            if(p[0] == s-1 and p[1] == s-1) return p[2];
            for(int i=0; i<8; i++){
                int x = p[0] + xy[i][0];
                int y = p[1] + xy[i][1];
                if(x<0 or x>=s or y<0 or y>=s or grid[x][y]) continue;
                else{
                    grid[x][y] = 1;
                    q.push({x,y,p[2]+1});
                }
            }
            q.pop();
        }
        return -1;
    }
};
```

