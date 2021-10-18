---
layout: post
title:  Cyclically Rotating a Grid
description: 
summary: 
tags:
    - array
    - matrix
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/cyclically-rotating-a-grid/)
You are given an `m x n` integer matrix `grid`​​​, where `m` and `n` are both even integers, and an integer `k`.

The matrix is composed of several layers, which is shown in the below image, where each color is its own layer:  
 <img src="https://assets.leetcode.com/uploads/2021/06/10/ringofgrid.png">  

A cyclic rotation of the matrix is done by cyclically rotating each layer in the matrix. To cyclically rotate a layer once, each element in the layer will take the place of the adjacent element in the counter-clockwise direction. An example rotation is shown below:  

<img src="https://assets.leetcode.com/uploads/2021/06/22/explanation_grid.jpg">   
Return *the matrix after applying k cyclic rotations to it.*


### Examples   

**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2021/06/19/rod2.png"> 
```
Input: grid = [[40,10],[30,20]], k = 1
Output: [[10,20],[40,30]]
Explanation: The figures above represent the grid at every state.
```

**Example 2:**  
<img src="https://assets.leetcode.com/uploads/2021/06/10/ringofgrid5.png">
<img src="https://assets.leetcode.com/uploads/2021/06/10/ringofgrid6.png">
<img src="https://assets.leetcode.com/uploads/2021/06/10/ringofgrid7.png">
```
Input: grid = [[1,2,3,4],[5,6,7,8],[9,10,11,12],[13,14,15,16]], k = 2
Output: [[3,4,8,12],[2,11,10,16],[1,7,6,15],[5,9,13,14]]
Explanation: The figures above represent the grid at every state.
```

### Constraints
+ `m == grid.length`
+ `n == grid[i].length`
+ `2 <= m, n <= 50`
+ Both `m` and `n` are even integers.
+ `1 <= grid[i][j] <= 5000`
+ `1 <= k <= 10^9`

## Solutions

```cpp
class Solution {
public:
    vector<vector<int>> rotateGrid(vector<vector<int>>& grid, int k) {
        int n = grid.size();
        int m = grid[0].size();
        int l=0,u=0,r=m-1,d=n-1;
        int level = min(m,n) / 2;
        while(level--){
            vector<int> temp;
            for(int i=l; i<=r; i++)
                temp.push_back(grid[u][i]);
            for(int i=u+1; i<=d; i++)
                temp.push_back(grid[i][r]);
            for(int i=r-1; i>=l; i--)
                temp.push_back(grid[d][i]);
            for(int i=d-1; i>u; i--)
                temp.push_back(grid[i][l]);
            
            int tsz = temp.size();
            int ti=0;
            for(int i=l; i<=r; i++,ti++)
                grid[u][i] = temp[(k+ti)%tsz];
            for(int i=u+1; i<=d; i++,ti++)
                grid[i][r] = temp[(k+ti)%tsz];
            for(int i=r-1; i>=l; i--,ti++)
                grid[d][i] = temp[(k+ti)%tsz];
            for(int i=d-1; i>u; i--,ti++)
                grid[i][l] = temp[(k+ti)%tsz];
            
            l++; r--;
            u++; d--;
        }
        
        return grid;
    }
};
```

