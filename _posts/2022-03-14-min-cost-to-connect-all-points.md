---
layout: post
title: Min Cost to Connect All Points
summary:
tags:
    - minimum-spannning-tree
    - leetcode
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/min-cost-to-connect-all-points)  

You are given an array points representing integer coordinates of some points on a 2D-plane, where points`[i] = [xi, yi]`.

The cost of connecting two points `[xi, yi]` and `[xj, yj]` is the **manhattan distance** between them: `|xi - xj| + |yi - yj|`, where `|val|` denotes the absolute value of `val`.

Return *the minimum cost to make all points connected*. All points are connected if there is exactly one simple path between any two points.

### Examples
**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2020/08/26/d.png">
```
Input: points = [[0,0],[2,2],[3,10],[5,2],[7,0]]
Output: 20
Explanation: 
```
<img src="https://assets.leetcode.com/uploads/2020/08/26/c.png">   
  
```
We can connect the points as shown above to get the minimum cost of 20.
Notice that there is a unique path between every pair of points.
```

**Example 2:**  
```
Input: points = [[3,12],[-2,5],[-4,1]]
Output: 18
```

### Constraints

+ `1 <= points.length <= 1000`
+ `-10^6 <= xi, yi <= 10^6`
+ All pairs `(xi, yi)` are distinct

## Solutions

```cpp
class Solution {
public:
    int minCostConnectPoints(vector<vector<int>>& points) {
      int V = points.size();
      vector<vector<int>> g(V,vector<int>(V,0));
      for(int i=0; i<V; i++){
        for(int j=0; j<V; j++){
          if(i==j) g[i][j]=0;
          else g[i][j] = abs(points[i][0]-points[j][0]) + abs(points[i][1]-points[j][1]) ;
        }
      }
      int key[V];
      fill(key, key+V, INT_MAX);
      int res = 0;
      key[0]=0;
      vector<bool> mSet(V,false);
      for(int i=0; i<V; i++){
        int u=-1;
        for(int v=0; v<V; v++)
          if(!mSet[v] and (u==-1 or key[v]<key[u]))
            u = v;
        mSet[u]=true;
        res += key[u];
        for(int v=0; v<V; v++)
          if(g[u][v] and !mSet[v])
            key[v] = min(key[v], g[u][v]);
      }
      return res;
    }
};
```