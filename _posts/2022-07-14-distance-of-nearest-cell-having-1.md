---
layout: post
title: Distance of nearest cell having 1                  
summary:
tags:
    - graph
    - matrix
    - bfs
    - geeksforgeeks
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/distance-of-nearest-cell-having-1-1587115620/0/?track=DSASP-Graph&batchId=154)  

Given a binary grid of `n*m`. Find the distance of the nearest `1` in the grid for each cell.
The distance is calculated as |`i1  - i2`| + |`j1 - j2`|, where `i1, j1` are the row number and column number of the current cell, and `i2, j2` are the row number and column number of the nearest cell having value `1`.

**Your Task:** 
You don't need to read or print anything, Your task is to complete the function `nearest()` which takes the grid as an input parameter and returns a matrix of the same dimensions where the value at index (`i, j`) in the resultant matrix signifies the minimum distance of `1` in the matrix from `grid[i][j]`.


**Expected Time Complexity:** `O(n*m)`           
**Expected Auxiliary Space:** `O(n*m)`


### Examples

**Example 1:**   
```
Input: grid = {{0,1,1,0},{1,1,0,0},{0,0,1,1}}
Output: {{1,0,0,1},{0,0,1,1},{1,1,0,0}}
Explanation: The grid is-
0 1 1 0 
1 1 0 0 
0 0 1 1 
0's at (0,0), (0,3), (1,2), (1,3), (2,0) and
(2,1) are at a distance of 1 from 1's at (0,1),
(0,2), (0,2), (2,3), (1,0) and (1,1)
respectively.
```


**Example 2:**   
```
Input: grid = {{1,0,1},{1,1,0},{1,0,0}}
Output: {{0,1,0},{0,0,1},{0,1,2}}
Explanation: The grid is-
1 0 1
1 1 0
1 0 0
0's at (0,1), (1,2), (2,1) and (2,2) are at a 
distance of 1, 1, 1 and 2 from 1's at (0,0),
(0,2), (2,0) and (1,1) respectively.
``` 


### Constraints

+ `1 ≤ n, m ≤ 500`

## Solutions

```cpp
class Solution
{
    public:
    //Function to find distance of nearest 1 in the grid for each cell.
	vector<vector<int>>nearest(vector<vector<int>>grid)
	{
	    // Code here
	    int r=grid.size(),c=grid[0].size();
	    vector<vector<int>> res(r,vector<int>(c,INT_MAX));
	    queue<pair<int,int>> q;
	    for(int i=0;i<r;i++)
	        for(int j=0;j<c;j++)
	            if(grid[i][j]){
	                res[i][j] = 0;
	                grid[i][j] = -1;
	                q.push({i,j});
	            }
	   int xy[5] = { -1, 0, 1, 0, -1 };
	   while(!q.empty()){
	       int x = q.front().first;
	       int y = q.front().second;
	       q.pop();
	       for(int i=0;i<4;i++){
	           int xi=x+xy[i], yi=y+xy[i+1];
	           if(xi<0||xi==r||yi<0||yi==c||grid[xi][yi]==-1) continue;
	           res[xi][yi] = min(res[xi][yi],res[x][y]+1);
	           q.push({xi,yi});
	           grid[xi][yi]=-1;
	       }
	   }
	   return res;
	    
	}
};
```

