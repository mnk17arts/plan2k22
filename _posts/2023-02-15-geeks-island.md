---
layout: post
title: Geeks Island
summary:
tags:
    - geeksforgeeks
    - dfs
    - bfs
    - matrix
    - cpp
    - medium
minute: 15+ min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/234ca3b438298fb04befd5abe7fbd98c006d4884/1) 

Geeks Island is represented by an N * M matrix mat. The island is touched by the Indian Ocean from the top and left edges and the Arabian Sea from the right and bottom edges. Each element of the matrix represents the height of the cell.

Due to the rainy season, the island receives a lot of rainfall, and the water can flow in four directions(up, down, left, or right) from one cell to another one with height equal or lower.

You need to find the number of cells from where water can flow to both the Indian Ocean and the Arabian Sea.

**Your Task:** 

Your task is to complete the function water_flow() which takes an integer array mat, integer N and integer M as the input parameter and returns an integer, denoting the number of cells from which water can to both ocean and sea.



**Expected Time Complexity:** `O(N*M)`  
**Expected Auxiliary Space:** `O(N*M)`  



### Examples

**Example 1:**   
```
Input:
N = 5, M = 5
mat[][] =    [[1, 3, 3, 2, 4],
               [4, 5, 6, 4, 4],
               [2, 4, 5, 3, 1],
               [6, 7, 1, 4, 5],
               [6, 1, 1, 3, 4]]
Output:
8
Explanation:
Indian    ~   ~   ~   ~   ~
Ocean  ~  1   3   3   2  (4) *
        ~  4   5  (6) (4) (4) *
        ~  2   4  (5)  3   1  *
        ~ (6) (7)  1   4   5  *
        ~ (6)  1   1   3   4  *           
           *   *   *   *   * Arabian Sea
Water can flow to both ocean and sea from the cells
denoted by parantheses().For example at index(1,2), the height of that island is 6. If a water drop falls on that island, water can flow to up direction(as 3<=6) and reach to Indian Ocean. ALso, water can flow to right direction(as 6>=4>=4) and reach to Arabian Sea.
```

**Example 2:** 
```
Input:
N = 3, M = 2
mat[][] =    [[1, 1, 1],
               [1, 1, 1]]
Output:
6 
Explanation:
Water can flow from all cells to both Indian Ocean and Arabian Sea as the height of all islands are same.
```

### Constraints

+ `1 <= N, M <= 10^3`
+ `1 <= mat[i][j] <= 10^6`

## Solutions

```cpp

class Solution{   
    bool valid(int i, int j, vector<vector<bool>> &vis, int prev, vector<vector<int>> &mat) {
        int n = vis.size(), m = vis[0].size();
        return i >=0 && j >= 0 && i < n && j < m && !vis[i][j] && prev <= mat[i][j];
    }
public:
    int water_flow(vector<vector<int>> &mat, int n, int m){
        queue<pair<int, pair<int, int>>> q;
        vector<vector<bool>> vis(n, vector<bool> (m, false));
        for(int i = 0; i < m; i++) {
           q.push({mat[0][i], {0, i}});
           vis[0][i] = 1;
        }
        for(int i = 1; i< n; i++) {
           q.push({mat[i][0], {i, 0}});
           vis[i][0] = 1;
        }
        map<pair<int, int>, int> indian;
        while(!q.empty()) {
           int val = q.front().first;
           pair<int, int> p = q.front().second;
           int i = p.first, j = p.second;
           q.pop();
           indian[{i, j}] = true;
           vis[i][j] = true;
           if(valid(i+1, j, vis, val, mat)){
                vis[i+1][j] = true;
                q.push({mat[i+1][j], {i+1, j}});
            }
            if(valid(i-1, j, vis, val, mat)){
                vis[i-1][j] = 1;
                q.push({mat[i-1][j], {i-1, j}});
            }
            if(valid(i, j-1, vis, val, mat)){
                vis[i][j-1] = 1;
                q.push({mat[i][j-1], {i, j-1}});
            }
            if(valid(i, j+1, vis, val, mat)){
                vis[i][j+1] = 1;
                q.push({mat[i][j+1], {i, j+1}});
            }
        }

        vector<vector<bool>> vi(n, vector<bool> (m, false));
        for(int i = 0; i < n; i++) {
            q.push({mat[i][m-1], {i, m-1}});
            vi[i][m-1] = true;
        }
        for(int j = 0; j < m-1; j++) {
            q.push({mat[n-1][j], {n-1, j}});
            vi[n-1][j] = 1;
        }
        int cnt = 0;
        while(!q.empty()) {
            int val = q.front().first;
            pair<int, int> p = q.front().second;
            int i = p.first, j = p.second;
            q.pop();
            if(indian[{i, j}]) {
                cnt++;
            }
            vi[i][j] = true;
            if(valid(i+1, j, vi, val, mat)) {
                vi[i+1][j] = true;
                q.push({mat[i+1][j], {i+1, j}});
            }
            if(valid(i-1, j, vi, val, mat)) {
                vi[i-1][j] = 1;
                q.push({mat[i-1][j], {i-1, j}});
            }
            if(valid(i, j-1, vi, val, mat)) {
                vi[i][j-1] = 1;
                q.push({mat[i][j-1], {i, j-1}});
            }
            if(valid(i, j+1, vi, val, mat)) {
                vi[i][j+1] = 1;
                q.push({mat[i][j+1], {i, j+1}});
            }
        }
        return cnt;
    }
};

```
