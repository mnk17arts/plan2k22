---
layout: post
title: X Total Shapes                  
summary:
tags:
    - graph
    - geeksforgeeks
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/x-total-shapes3617/0/?track=DSASP-Graph&batchId=154)  

Given  a grid of `n*m` consisting of `O`'s and `X`'s. The task is to find the number of '`X`' total shapes.
Note: '`X`' shape consists of one or more adjacent `X`'s (diagonals not included).

**Your Task:** 

You don't need to read or print anything. Your task is to complete the function `xShape()` which takes grid as input parameter and returns the count of total `X` shapes.


**Expected Time Complexity:** `O(n*m)`           
**Expected Auxiliary Space:** `O(n*m)`


### Examples

**Example 1:**   
```
Input: grid = [[X,O,X],[O,X,O],[X,X,X]]
Output: 3
Explanation: 
The grid is-
X O X
O X O
X X X
there are 3 different groups 
in the given grid.

```


**Example 2:**   
```
Input: grid = [[X,X],[X,X]]
Output: 1
Expanation: 
The grid is- 
X X
X X
there is only 1 group
in the given grid.
``` 


### Constraints

+ `1 ≤ n, m ≤ 100`

## Solutions

```cpp
class Solution
{
    public:
 	void dfs(int i,int j,vector<vector<char>>& grid,int m,int n){
        if(i<0 || j<0 || i>=m || j>=n || grid[i][j]!='X') return;
        grid[i][j]='Z';
        dfs(i+1,j,grid,m,n);
        dfs(i,j+1,grid,m,n);
        dfs(i,j-1,grid,m,n);
        dfs(i-1,j,grid,m,n);
    }
    //Function to find the number of 'X' total shapes.
    int xShape(vector<vector<char>>& grid) 
    {
        // Code here
        int m=grid.size(),n=grid[0].size();
        int ans=0;
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(grid[i][j]=='X'){
                    ans++;
                    dfs(i,j,grid,m,n);
                }
            }
        }
        return ans;
    }
};
```

