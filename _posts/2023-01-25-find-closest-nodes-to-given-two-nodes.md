---
layout: post
title: Find Closest Node to Given Two Nodes                       
summary:
tags:
    - leetcode
    - graph
    - dfs
    - cpp
    - medium
minute: 10+ min
---

## Problem Statement - [*link*](https://leetcode.com/problems/find-closest-node-to-given-two-nodes/description/)  

You are given a directed graph of n nodes numbered from 0 to n - 1, where each node has at most one outgoing edge.

The graph is represented with a given 0-indexed array edges of size n, indicating that there is a directed edge from node i to node edges[i]. If there is no outgoing edge from i, then edges[i] == -1.

You are also given two integers node1 and node2.

Return the index of the node that can be reached from both node1 and node2, such that the maximum between the distance from node1 to that node, and from node2 to that node is minimized. If there are multiple answers, return the node with the smallest index, and if no possible answer exists, return -1.

Note that edges may contain cycles.

### Examples


**Example 1:**   
<img src="https://assets.leetcode.com/uploads/2022/06/07/graph4drawio-2.png">
```
Input: edges = [2,2,3,-1], node1 = 0, node2 = 1
Output: 2
Explanation: The distance from node 0 to node 2 is 1, and the distance from node 1 to node 2 is 1.
The maximum of those two distances is 1. It can be proven that we cannot get a node with a smaller maximum distance than 1, so we return node 2.
```


**Example 2:**   
<img src="https://assets.leetcode.com/uploads/2022/06/07/graph4drawio-4.png">
```
Input: edges = [1,2,-1], node1 = 0, node2 = 2
Output: 2
Explanation: The distance from node 0 to node 2 is 2, and the distance from node 2 to itself is 0.
The maximum of those two distances is 2. It can be proven that we cannot get a node with a smaller maximum distance than 2, so we return node 2.
```


### Constraints

+ `n == edges.length`
+ `2 <= n <= 10^5`
+ `-1 <= edges[i] < n`
+ `edges[i] != i`
+ `0 <= node1, node2 < n`

## Solutions

```cpp
class Solution {
public:
    void dfs(vector<int>& edges, int node, vector<bool>& vis, vector<int>& dis) {
        vis[node] = true;
        int next = edges[node];
        if( next!=-1 && !vis[next] ) {
            dis[next] = dis[node] + 1;
            dfs(edges, next, vis, dis);
        }
    }
    int closestMeetingNode(vector<int>& edges, int node1, int node2) {
        int n = edges.size();
        vector<bool> vis1(n, false), vis2(n, false);
        vector<int> dis1(n, 0), dis2(n, 0);
        int res = -1, mdis = INT_MAX;
        dfs(edges, node1, vis1, dis1);
        dfs(edges, node2, vis2, dis2);
        for( int i = 0; i < n; i++ ) {
            if( vis1[i] && vis2[i] && mdis > max(dis1[i],dis2[i]) ) {
                mdis = max(dis1[i], dis2[i]);
                res = i;
            }
        }
        return res;
    }
};
```

