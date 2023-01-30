---
layout: post
title: Select Nodes                     
summary:
tags:
    - geeksforgeeks
    - dynamic-programming
    - tree
    - dfs
    - cpp
    - hard
minute: 15+ min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/f7bfa137576243795abb0595962d61b632bbad21/1)  

Given N nodes of a tree and a list of edges. Find the minimum number of nodes to be selected to light up all the edges of the tree.

An edge lights up when at least one node at the end of the edge is selected

**Your Task:** 

You don't need to read input or print anything. Your task is to complete the function countVertex() which takes the number of nodes N, and the list of edges as input parameters and returns the minimum number of nodes selected.


**Expected Time Complexity:** `O(N)`              
**Expected Auxiliary Space:** `O(N)` 



### Examples

**Example 1:**   
```
Input:
N = 6
edges[] = [[1,2], [1,3], [2,4], [3,5], [3,6]]
Output: 2
Explanation: Selecting nodes 2 and 3 lights
up all the edges.
```

**Example 2:**   
```
Input:
N = 3
arr[] = [[1,2], [1,3]]
Output: 1
Explanation: Selecting Node 1 
lights up all the edges.
```

### Constraints

+ `1 ≤ N ≤ 10^5`
+ `1 ≤ edges[i][0], edges[i][1] ≤ N`
+ given graph is a valid tree

## Solutions

```cpp

class Solution{
  public:
  
    bool dfs(vector<vector<int>> &ed, vector<bool> &vis, int id, int &res) {
        vis[id] = true;
        bool flag = false;
        for(int e: ed[id]) {
            if(!vis[e] && !dfs(ed, vis, e, res)) {
                flag = true;
            }
        }
        if(flag) {
            res++;
        }
        return flag;
    }
  
    int countVertex(int N, vector<vector<int>>edges){
        // code here
        vector<vector<int>> ed(N+1);
        vector<bool> vis(N+1, 0);
        for(auto i: edges) {
            ed[i[0]].push_back(i[1]);
            ed[i[1]].push_back(i[0]);
        }
        int res=0;
        dfs(ed, vis, 1, res);
        return res;
    }
};

```

