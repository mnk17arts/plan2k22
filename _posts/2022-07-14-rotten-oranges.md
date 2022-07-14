---
layout: post
title: Rotten Oranges                   
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

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/rotten-oranges2536/0/?track=DSASP-Graph&batchId=154#)  

Given a grid of dimension nxm where each cell in the grid can have values `0`, `1` or `2` which has the following meaning:
`0` : Empty cell
`1` : Cells have fresh oranges
`2` : Cells have rotten oranges

We have to determine what is the minimum time required to rot all oranges. A rotten orange at index `[i,j]` can rot other fresh orange at indexes `[i-1,j], [i+1,j], [i,j-1], [i,j+1]` (up, down, left and right) in unit time. 

**Your Task:** 
You don't need to read or print anything, Your task is to complete the function `orangesRotting()` which takes grid as input parameter and returns the minimum time to rot all the fresh oranges. If not possible returns `-1`.


**Expected Time Complexity:** `O(n*m)`           
**Expected Auxiliary Space:** `O(n)`


### Examples

**Example 1:**   
```
Input: grid = [[2,2,0,1]]
Output: -1
Explanation: The grid is-
2 2 0 1
Oranges at (0,0) and (0,1) can't rot orange at
(0,3).
```

**Example 2:**   
```
Input: grid = [[0,1]]
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
    //Function to find minimum time required to rot all oranges. 
    int orangesRotting(vector<vector<int>>& grid) {
        // Code here
        int xy[5] = { -1,0,1,0,-1 };
        int m = grid.size(), n = grid[0].size();
        queue<vector<int>> q;
        for(int i=0;i<m;i++)
            for(int j=0;j<n;j++)
                if(grid[i][j]==2)
                    q.push({i,j,0});
        int res; 
        while(!q.empty()){
            int x=q.front()[0];
            int y=q.front()[1];
            res =q.front()[2];
            q.pop();
            for(int i=0;i<4;i++)
                if( x+xy[i] < 0 || x+xy[i]==m ||
                y+xy[i+1] < 0 || y+xy[i+1]==n ||
                  grid[x+xy[i]][y+xy[i+1]]!=1 )
                  continue;
                else {
                    grid[x+xy[i]][y+xy[i+1]]=2;
                    q.push({x+xy[i],y+xy[i+1],res+1});
                }
        }
        for(auto i: grid)
            for(int j: i)
                if(j==1)
                    return -1;
        return res;
    }
};
```

