---
layout: post
title: Mother Vertex                  
summary:
tags:
    - graph
    - dfs
    - geeksforgeeks
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/mother-vertex/0/?track=DSASP-Graph&batchId=154#)  

Given a Directed Graph, find a Mother Vertex in the Graph (if present). 
A Mother Vertex is a vertex through which we can reach all the other vertices of the Graph.

**Your Task:** 
You don't need to read or print anything. Your task is to complete the function `findMotherVertex()` which takes `V` denoting the number of vertices and adjacency list as imput parameter and returns the verticex from through which we can traverse all other vertices of the graph. If there is more than one possible nodes then returns the node with minimum value.If not possible returns `-1`.


**Expected Time Complexity:** `O(V + E)`           
**Expected Auxiliary Space:** `O(V)`


### Examples

**Example 1:**   
```
Input:
```

<img src="data:image/png;base64,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">

```
Output: 0
Explanation: According to the given edges, all 
nodes can be reaced from nodes from 0, 1 and 2. 
But, since 0 is minimum among 0,1 and 3, so 0 
is the output.
```



### Constraints

+ `1 ≤ V ≤ 500`

## Solutions

```cpp
class Solution
{
    public:
    void dfs(int v,vector<int> adj[],vector<int>&vis,stack<int>&st,bool check){
        vis[v]=1;
        for(int w: adj[v])
            if(!vis[w])
                dfs(w,adj,vis,st,check);
        if(check) st.push(v);
    }
    //Function to find a Mother Vertex in the Graph.
	int findMotherVertex(int V, vector<int>adj[])
	{
	    // Code here
	    vector<int> vis(V);
	    stack<int> st;
	    for(int i=0;i<V;i++)
	        if(!vis[i])
	            dfs(i,adj,vis,st,1);
	    int res=st.top();
	    fill(vis.begin(),vis.end(),0);
	    dfs(res,adj,vis,st,0);
	    int v = accumulate(vis.begin(),vis.end(),0);
	    if(v!=V) res = -1;
	    return res;
	}
};
```

