---
layout: post
title: Number of Connected Components                   
summary:
tags:
    - disjoint-set
    - graph
    - geeksforgeeks
    - cpp
    - easy
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/number-of-connected-components/0/?track=DSASP-DisjointSet&batchId=154#)  

This problem is to find the number of connected components. There will be 2 incomplete functions namely unionNodes and findNumberOfConnectedNodes. You have to complete these functions. 

unionNodes: Join two subsets into a single set.
findNumberOfConnectedNodes: Determine number of different connected components in a graph. 

**Your Task:** 
You have to complete the function unionNodes() which merges the node1 and node2. You will also have to complete the function findNumberOfConnectedNodes() function will returntotal number of different connected components in a graph..


**Expected Time Complexity:** `O(N)`           
**Expected Auxiliary Space:** `O(1)`


### Examples

**Example 1:**   
```
Input:
N = 5
M = 2
Edges[] = {(1,3),(1,5)}
Output: 3
Explanation: Initially all nodes 1 2 3 4 5
are not connected. 
After 1 3, node 1 and 3 will be connected.
After 1 5, node 1 and 5 will be connected.
Finally we have {1,3,5}, {2}, {4}. So we
have a total of 3 connected components.
```

**Example 2:**   
```
Input:
N = 5
M = 4
Edges[] = {(1,4),(2,3),(1,5)}
Output: 2
Explanation: Initially all nodes 1 2 3 4 5
are not connected.
After 1 4, node 1 and 4 will be connected.
After 2 3, node 2 and 3 will be connected.
After 1 5, node 1 and 5 will be connected.
Finally we have {1,4,5}, {2, 3}. So we
have total of 2 connected components
```

### Constraints

+ `1 ≤ N , M ≤ 10^5`
+ `1 ≤ Edges[i][0], Edges[i][1] ≤ N`

## Solutions

```cpp
class Solution
{
    public:
    int find(int x,int arr[]){
        if(arr[x]!=x){
            arr[x]=find(arr[x],arr);
        }
        return arr[x];
    }
    //Function to merge two nodes a and b.
    void unionNodes( int a, int b, int arr[], int rank1[], int n) 
    {
        //code here
        a = find(a,arr);
        b = find(b,arr);
        if(a==b) return;
        if(rank1[a]>rank1[b])
            arr[b]=a;
        else arr[a]=b;
        if(rank1[a]==rank1[b]) rank1[a]++;
    }
    
    //Function to determine number of connected components.
    int findNumberOfConnectedComponents( int n, int arr[], int rank1[]) 
    {
        //code here
        unordered_set<int> s;
        for(int i=1;i<=n;i++)
            s.insert(find(i,arr));

        return s.size();
    }
};
```

