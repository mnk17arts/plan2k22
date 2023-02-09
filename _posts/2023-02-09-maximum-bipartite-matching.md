---
layout: post
title: Maximum Bipartite Matching
summary:
tags:
    - geeksforgeeks
    - matrix
    - graph
    - dfs
    - cpp
    - medium
minute: 10+ min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/9a88fe7ada1c49c2b3da7a67b43875e4a76aface/1) 

There are M job applicants and N jobs.  Each applicant has a subset of jobs that he/she is interested in. Each job opening can only accept one applicant and a job applicant can be appointed for only one job. Given a matrix G with M rows and N columns where G(i,j) denotes ith applicant is interested in the jth job. Find the maximum number of applicants who can get the job.

**Your Task:** 

You don't need to read to print anything. Your task is to complete the function maximumMatch() which takes matrix G as input parameter and returns the maximum number of applicants who can get the job.



**Expected Time Complexity:** `O(N^3)`  
**Expected Auxiliary Space:** `O(N)`  



### Examples

**Example 1:**   
```
Input: 
M = 3, N = 5
G = [[1,1,0,1,1],[0,1,0,0,1],
[1,1,0,1,1]]
Output: 3
Explanation: There is one of the possible
assignment-
First applicant gets the 1st job.
Second applicant gets the 2nd job.
Third applicant gets the 4th job.
```

**Example 2:** 
```
Input:
M = 6, N = 2
G = [[1,1],[0,1],[0,1],[0,1],
[0,1],[1,0]]
Output: 2
Explanation: There is one of the possible
assignment-
First applicant gets the 1st job.
Second applicant gets the 2nd job.
```

### Constraints

+ `1 ≤ N, M ≤ 100`

## Solutions

```cpp

class Solution{
  public:
  bool dfs(vector<vector<int>> &G, int m, vector<bool> &taken, vector<int> &valid) {
        for(int n = 0; n < G[0].size(); n++) {
            if(G[m][n] == 1 && !taken[n]) {
                taken[n] = true;
                if(valid[n] == -1 || dfs(G, valid[n], taken, valid)) {
                    valid[n] = m;
                    return true;
                }
            }
        }
        return false;
  }
	int maximumMatch(vector<vector<int>>&G){
	    // Code here
	    int M = G.size();
	    int N = G[0].size();
	    vector<int> valid(N, -1);
	    int res = 0;
	    for (int i = 0; i < M; i++) {
	        vector<bool> taken(N, false);
	        if(dfs(G, i, taken, valid)) {
	            res++;
	        }
	    }
	    return res;
	}
};

```
