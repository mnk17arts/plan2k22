---
layout: post
title: Largest Sum Cycle                     
summary:
tags:
    - geeksforgeeks
    - graph
    - backtracking
    - cpp
    - hard
minute: 15+ min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/51afa710a708c0681748445b509696dd588d5c40/1)  

Given a maze with N cells. Each cell may have multiple entry points but not more than one exit(i.e entry/exit points are unidirectional doors like valves).

You are given an array Edge[] of N integers, where Edge[i] contains the cell number that can be reached from of cell i in one step. Edge[i] is -1 if the ith cell doesn't have an exit. 
The task is to find the largest sum of a cycle in the maze(Sum of a cycle is the sum of the cell indexes of all cells present in that cycle).

Note:The cells are named with an integer value from 0 to N-1. If there is no cycle in the graph then return -1.

**Your Task:** 

You dont need to read input or print anything. Your task is to complete the function largestSumCycle() which takes the integer N denoting the number of cells and the array Edge[] as input parameters and returns the sum of the largest sum cycle in the maze.



**Expected Time Complexity:** `O(N)`              
**Expected Auxiliary Space:** `O(N)` 



### Examples

**Example 1:**   
```
Input:
N = 4
Edge[] = {1, 2, 0, -1}
Output: 3
Explanation: 
There is only one cycle in the graph.
(i.e 0->1->2->0)
Sum of the cell index in that cycle 
= 0 + 1 + 2 = 3.
```

**Example 2:**   
```
Input:
N = 4 
Edge[] = {2, 0, -1, 2}
Output: -1
Explanation:
1 -> 0 -> 2 <- 3
There is no cycle in the graph.
```

### Constraints

+ `1 <= N <= 10^5`
+ `-1 < Edge[i] < N`
+ `Edge[i] != i`

## Solutions

```cpp

class Solution{   
  public:
  long long ans = -1;
  
  void solve(vector<int> &Edge, int i, long long sum, vector<bool> &visit, vector<long long> &inc) {
      
      if(inc[i] > -1) {
          ans = max(ans, sum - inc[i] + i);
          return;
      }
      
      if(visit[i] == true) {
          return;
      }
        
      visit[i] = true;
      inc[i] = sum+i;

      if(Edge[i]!=-1) {
          solve(Edge,Edge[i],sum+i,visit,inc);
      }
      inc[i]=-1;
  }

  long long largestSumCycle(int N, vector<int> Edge) {
      
        vector<bool> visit(N,false);
        vector<long long> inc(N,-1);
        
        for(int i=0;i<N;i++)    {
            if(visit[i]==false) {
                solve(Edge,i,0,visit,inc);
            }
        }
        
        return ans;
  }
};

```

