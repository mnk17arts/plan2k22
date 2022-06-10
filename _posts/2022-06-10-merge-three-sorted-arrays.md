---
layout: post
title: Merge three sorted arrays 
summary:
tags:
    - sorting
    - math
    - array
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/merge-three-sorted-arrays-1587115620/0/#)  

Given three sorted arrays `A`, `B` and `C` of size `N`, `M` and `P` respectively. The task is to merge them into a single array which must be sorted in increasing order.

**Your Task:** 
This is a function problem. You only need to complete the function `mergeThree()` that takes `A,B,C` as parameters. The function returns an array or vector.

**Expected Time Complexity:** `O(N + M + P)`  
**Expected Auxiliary Space:** `O(N + M + P)` for the resultant array only



### Examples

**Example 1:**   
```
Input: 
N = 4, A[] = [1 2 3 4] 
M = 5, B[] = [1 2 3 4 5] 
P = 6, C[] = [1 2 3 4 5 6]
Output: 1 1 1 2 2 2 3 3 3 4 4 4 5 5 6
Explanation: Merging these three sorted 
arrays, we have: 
1 1 1 2 2 2 3 3 3 4 4 4 5 5 6.
```

**Example 2:**   
```
Input: 
N = 2, A[] = [1 2]
M = 3, B[] = [2 3 4] 
P = 4, C[] = [4 5 6 7]
Output: 1 2 2 3 4 4 5 6 7
Explanation: Merging three sorted arrays, 
we have: 1 2 2 3 4 4 5 6 7.
```

### Constraints

+ `1 <= N, M, P <= 10^6`
+ `1 <= A[i], B[i], C[i] <= 10^6`

## Solutions

```cpp
class Solution{
    public:
    // A, B, and C: input sorted arrays
    //Function to merge three sorted vectors or arrays 
    //into a single vector or array.
    void merge(vector<int>& abc, int i, vector<int>& a, int j){
        while(j<a.size())
            abc[i++] = a[j++];
    }
    void mergeTwo(vector<int>& abc, int x, vector<int>& a, int i, vector<int>& b, int j){
        int n = a.size(), m = b.size();
        while(i<n && j<m)
            if(a[i] <= b[j]) abc[x++] = a[i++];
            else abc[x++] = b[j++];
        if(i==n) merge(abc, x, b, j);
        else if(j==m) merge(abc, x, a, i);
    }
    vector<int> mergeThree(vector<int>& A, vector<int>& B, vector<int>& C) 
    { 
        //Your code here
        int n = A.size(), m = B.size(), p = C.size();
        vector<int> abc(n+m+p);
        int i=0, j=0, k=0, x=0;
        while(i<n && j<m && k<p)
            if(A[i] <= B[j] && A[i] <= C[k]) abc[x++] = A[i++];
            else if (B[j] <= C[k]) abc[x++] = B[j++];
            else abc[x++] = C[k++];
        if(i==n) mergeTwo(abc, x, B, j, C, k);
        else if(j==m) mergeTwo(abc, x, A, i, C, k);
        else if(k==p) mergeTwo(abc, x, A, i, B, j);
        
        return abc;
    } 

};
```

