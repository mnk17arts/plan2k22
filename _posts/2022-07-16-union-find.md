---
layout: post
title: Union-Find                   
summary:
tags:
    - disjoint-set
    - graph
    - geeksforgeeks
    - cpp
    - easy
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/union-find/0/?track=DSASP-DisjointSet&batchId=154)  

This problem is to implement disjoint set union. There will be 2 incomplete functions namely union and find. You have to complete these functions. 

Union: Join two subsets into a single set.
isConnected: Determine which subset a particular element is in. This can be used for determining if two elements are in same subset.

**Your Task:** 
You have to complete the function union_() which merges the node1 and node2. You will also have to complete the function isConnected() which will return whether the two nodes are connected.

Note: Both function will contain two arrays par[] and ranks1[] along with two nodes. Initially par[i] = i and rank1[i] = 1 


**Expected Time Complexity:** `O(N+Q)`           
**Expected Auxiliary Space:** `O(1)`


### Examples

**Example 1:**   
```
Input:
N = 5
q = 4
Queries = 
Union(1,3)
isConnected(1,2)
Union(1,5)
isConnected(3,5)
Output:
0
1
Explanation: Initially all nodes 1 2 3 4 5
are not connected. 
After Union(1,3), node 1 and 3 will be
connected.
When we do isConnected(1,2),  as node 1
and 2 are not connected it will return 0.
After Union(1,5), node 1 and 5 will be
connected.
When we do isConnected(3,5),  as node
1 and 3 are connected, and node 1 and 5
are connected, hence 3 and 5 are
connected. Thus it will return 1.
```

**Example 2:**   
```
Input:
N = 5
q = 4
Queries = 
Union(1,4)
Union(1,5)
isConnected(2,3)
Union(3,4)
Output: 0
```

### Constraints

+ `1 ≤ N , Q ≤ 10^5`
+ `1 ≤ Edges[i][0], Edges[i][1] ≤ N`

## Solutions

```cpp
class Solution
{
    public:
    //Function to merge two nodes a and b.
    void union_( int a, int b, int par[], int rank1[]) 
    {
        //code here
        a = find(a,par);
        b = find(b,par);
        if(rank1[a]>rank1[b])
            par[b]=a;
        else par[a]=b;
        if(rank1[a]==rank1[b]) rank1[a]++;
    }
    
    int find(int x,int par[]){
        if(par[x]!=x){
            par[x]=find(par[x],par);
        }
        return par[x];
    }
    
    //Function to check whether 2 nodes are connected or not.
    bool isConnected(int x,int y, int par[], int rank1[])
    {
        //code here
        return find(x,par)==find(y,par);
    }
};
```

