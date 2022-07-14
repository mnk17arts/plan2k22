---
layout: post
title:  Minimum Cost Path                    
summary:
tags:
    - graph
    - greedy
    - geeksforgeeks
    - cpp
    - medium
minute: 12 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/minimum-cost-path3833/0/?track=DSASP-Graph&batchId=154)  

Given a square grid of size `N`, each cell of which contains integer cost which represents a cost to traverse through that cell, we need to find a path from top left cell to bottom right cell by which the total cost incurred is minimum.
From the cell `(i,j)` we can go `(i,j-1), (i, j+1), (i-1, j), (i+1, j)`. 

Note: It is assumed that negative cost cycles do not exist in the input matrix.

**Your Task:** 
You don't need to read or print anything. Your task is to complete the function `minimumCostPath()` which takes grid as input parameter and returns the minimum cost to react at bottom right cell from top left cell.


**Expected Time Complexity:** `O(n^2 * log(n))`           
**Expected Auxiliary Space:** `O(n^2)`


### Examples

**Example 1:**   


```
Input: grid = [[9,4,9,9],[6,7,6,4],
[8,3,3,7],[7,4,9,10]]
Output: 43
Explanation: The grid is-
9 4 9 9
6 7 6 4
8 3 3 7
7 4 9 10
The minimum cost is-
9 + 4 + 7 + 3 + 3 + 7 + 10 = 43.
```

### Constraints

+ `1 ≤ n ≤ 500`
+ `1 ≤ cost of cells ≤ 1000`

## Solutions

```cpp
class Solution
{
    public:
    //Function to return the minimum cost to react at bottom
	//right cell from top left cell.
    int minimumCostPath(vector<vector<int>>& grid) 
    {
        // Code here
        int m=grid.size(), n = grid[0].size();
        vector<vector<int>> dis(m,vector<int>(n,INT_MAX));
        priority_queue<pair<int,pair<int,int>>,
                vector<pair<int,pair<int,int>>>,
                greater<pair<int,pair<int,int>>>> pq;
        dis[0][0] = grid[0][0];
        pq.push({dis[0][0],{0,0}});
        int a[5] = { -1,0,1,0,-1 };
        while(!pq.empty()){
            int d = pq.top().first;
            auto p = pq.top().second;
            int i = p.first;
            int j = p.second;
            pq.pop();
            if(i==m-1&&j==n-1) break;
            for(int k=0;k<4;k++){
                int x = i + a[k];
                int y = j + a[k+1];
                if(x<0||x==m||y<0||y==n) continue;
                if(dis[x][y] > dis[i][j] + grid[x][y]){
                    dis[x][y] = dis[i][j]+grid[x][y];
                    pq.push({dis[x][y],{x,y}});
                }
            }
        }
        return dis[m-1][n-1];
    }
};
```

