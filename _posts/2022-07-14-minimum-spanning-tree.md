---
layout: post
title: Minimum Spanning Tree                    
summary:
tags:
    - graph
    - geeksforgeeks
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/minimum-spanning-tree/0/?track=DSASP-Graph&batchId=154#)  

Given a weighted, undirected and connected graph of `V` vertices and `E` edges. The task is to find the sum of weights of the edges of the Minimum Spanning Tree.

**Your Task:** 
Since this is a functional problem you don't have to worry about input, you just have to complete the function  `spanningTree()` which takes number of vertices `V` and an adjacency matrix `adj` as input parameters and returns an integer denoting the sum of weights of the edges of the Minimum Spanning Tree. Here `adj[i]` contains a list of lists containing two integers where the first integer `a[i][0]` denotes that there is an edge between `i` and `a[i][0]` and second integer `a[i][1]` denotes that the distance between edge `i` and `a[i][0]` is `a[i][1]`.


**Expected Time Complexity:** `O(ElogV)`           
**Expected Auxiliary Space:** `O(V^2)`


### Examples

**Example 1:**   

<img src="data:image/png;base64,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">

```
Output:
5
Explanation:
Only one Spanning Tree is possible
which has a weight of 5.
```

### Constraints

+ `2 ≤ V ≤ 1000`
+ `V-1 ≤ E ≤ (V*(V-1))/2`
+ `1 ≤ w ≤ 1000`
+ Graph is connected and doesn't contain self loops & multiple edges.

## Solutions

```cpp
class Solution
{
    public:
	//Function to find sum of weights of edges of the Minimum Spanning Tree.
    int spanningTree(int V, vector<vector<int>> adj[]) {
        
       vector<bool> vis(V+1, false);
       priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> q;
       q.push({0, 0});
       int sum = 0;
       while(!q.empty())  {
           auto node = q.top();
           int u = node.second;
           int w = node.first;
           q.pop();
           if(!vis[u])  {
               for(auto n:adj[u])  {
                   if(!vis[n[0]])
                       q.push({n[1], n[0]});
               }
               vis[u] = true;
               sum+=w;
           }
       }
       return sum;
   }
};
```

