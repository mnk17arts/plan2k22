---
layout: post
title: Find whether path exist                
summary:
tags:
    - dfs
    - bfs
    - graph
    - matrix
    - geeksforgeeks
    - cpp
    - medium
minute: 12 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/find-whether-path-exist5238/0/?track=DSASP-Graph&batchId=154)  

Given a grid of size `n*n` filled with `0, 1, 2, 3`. Check whether there is a path possible from the source to destination. You can traverse up, down, right and left.
The description of cells is as follows:

+ A value of cell `1` means Source.
+ A value of cell `2` means Destination.
+ A value of cell `3` means Blank cell.
+ A value of cell `0` means Wall.
Note: There are only a single source and a single destination.

**Your Task:** 
You don't need to read or print anything. Your task is to complete the function `is_Possible()` which takes the grid as input parameter and returns boolean value 1 if there is a path otherwise returns 0.


**Expected Time Complexity:** `O(n*n)`       
**Expected Auxiliary Space:** `O(n*n)`


### Examples

**Example 1:**   
```
Input: grid = [[3,0,3,0,0],[3,0,0,0,3]
,[3,3,3,3,3],[0,2,3,0,0],[3,0,0,1,3]]
Output: 0
Explanation: The grid is-
3 0 3 0 0 
3 0 0 0 3 
3 3 3 3 3 
0 2 3 0 0 
3 0 0 1 3 
There is no path to reach at (3,1) i,e at 
destination from (4,3) i,e source.
``` 


### Constraints

+ `1 ≤ n ≤ 500`

## Solutions

```cpp
class Solution
{
    public:
    //Function to find whether a path exists from the source to destination.
    bool check(int i, int j, int n) {
       return !(i >= n || j >= n || i < 0 || j < 0) ;
    }
    bool is_Possible(vector<vector<int>>& grid) 
    {
       int n = grid.size();
       queue<pair<int, int>> q;
       for (int i = 0; i < n; i++) {
           for (int j = 0; j < n; j++) {
               if (grid[i][j] == 1) {
                   q.push({i, j});
                   grid[i][j] = 0;
               }
           }
       }
       int x[4] = {-1, 0, 1, 0};
       int y[4] = {0, -1, 0, 1};
       
       while (!q.empty()) {
           pair<int, int> node = q.front();
           q.pop();
           for (int k = 0; k < 4; k++) {
               int i = node.first + x[k];
               int j = node.second + y[k];
               if (check(i, j, n) && grid[i][j] != 0) {
                   q.push({i, j});
                   if (grid[i][j] == 2)
                       return true;
                   grid[i][j] = 0;
               }
           }
       }
       return false;
    }
};
```

