---
layout: post
title: Minimum Spanning Tree using Kruskal                     
summary:
tags:
    - disjoint-set
    - graph
    - geeksforgeeks
    - cpp
    - medium
minute: 12 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/minimum-spanning-tree3233/0/?track=DSASP-DisjointSet&batchId=154#)  

You are given a graph where each edge has a weight associated with it.  Find the minimum spanning tree value.

Minimum Spanning Tree: Given a connected and undirected graph, a spanning tree of that graph is a subgraph that is a tree and connects all the vertices together.  A single graph can have many different spanning trees.  A minimum spanning tree (MST) or minimum weight spanning tree for a weighted, connected and undirected graph is a spanning tree with weight less than or equal to the weight of every other spanning tree. The weight of a spanning tree is the sum of weights given to each edge of the spanning tree.

**Your Task:** 

You will have to complete the function `calcMinimumSpanningValue()` function will return the minimum spanning value.

Note:
Cpp: The graph is given as array of vector containing pairs `i`.e. if `adj[2] = (3,4)` it implies `src = 2`, `des = 3` `wt = 4`
Java: The graph is given as a Arraylist of a class Edge. Edge contains three variables- `src`, `des`, `wt`
Python: The graph is given by an array of triplets (`src,des,wt`) 


**Expected Time Complexity:** `O(N + M)`              
**Expected Auxiliary Space:** `O(N + M)`


### Examples


**Example 1:**   
```
Input:
N = 5, M = 6 
Edges[] = {(1,2,4),(1,3,3),(2,4,1),
           (2,5,1),(4,5,3),(3,4,2)}
Output: 7
Explanation: The tree will be formed from
these nodes and weights ,{1,3,3}, {2,4,1}
{2,5,1}, {3,4,2}. Total sum of these edges
is 7.
```

**Example 2:**   
```
Input:
N = 4, M = 5
Edges[] = {(1,2,5),(2,3,6),(1,4,7),
           (2,4,8),(3,4,7)}
Output: 18
Explanation: The tree will be formed from
these nodes and weights, {1,2,5}, {2,3,6},
{3,4,7}. Total sum of those edges is 18
```


### Constraints

+ `2 <= N <= 10^5`
+ `1 <= M <= 10^5`
+ `1 <= src, des <= N`
+ `1 <= wt <= 10^5`
+ Graph doesn't contains multiple edges or self loops

## Solutions

```cpp
struct edge{
    int u;
    int v;
    int wt;
    edge(int x, int y, int z){
        u = x;
        v = y;
        wt = z;
    };
};


bool static comp(struct edge &x, struct edge &y){
    return x.wt < y.wt;
}

int find(int i, vector<int> &par){
    if(i == par[i]){
        return i;
    }
    par[i] = find(par[i], par);
    return par[i];
}

void union_(int a, int b, vector<int> &par, vector<int> &rank){
    int a_rep = find(a, par);
    int b_rep = find(b, par);
    if(a_rep == b_rep){
        return;
    }
    if(rank[a_rep] > rank[b_rep]){
        par[b_rep] = a_rep;
    }
    else if(rank[a_rep] < rank[b_rep]){
        par[a_rep] = b_rep;
    }
    else{
        par[b_rep] = a_rep;
        rank[a_rep]++;
    }
}

long long int kruskalDSU(vector<pair<int, long long int>> adj[], int n, int m) 
{
       vector<edge> edges;
       for(int i = 1; i <= n; i++){
           for(auto &e : adj[i]){
               int v = e.first;
               int w = e.second;
               if(v > i){
                   edge myEdge(i, v, w);
                   edges.push_back(myEdge);
               }
           }
       }
        sort(edges.begin(), edges.end(), comp);
        vector<int> par(n + 1, 0);
        vector<int> rank(n + 1, 0);
        for(int i = 0; i <= n; i++){
            par[i] = i;
        }
        long long ans = 0;
        for(auto &ed : edges){
            int u = ed.u;
            int v = ed.v;
            int wt = ed.wt;
            if(find(u, par) != find(v, par)){
                union_(u, v, par, rank);
                ans += wt;
            }
        }
        return ans;
}
```

