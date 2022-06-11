---
layout: post
title: Kth element in Matrix  
summary:
tags:
    - matrix
    - binary-search
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/kth-element-in-matrix/1#)  

Given a `N x N` matrix, where every row and column is sorted in non-decreasing order. Find the `k`th smallest element in the matrix.

**Your Task:** 
You don't need to read input or print anything. Complete the function `kthsmallest()` which takes the `mat`, `N` and `K` as input parameters and returns the `k`th smallest element in the matrix.

**Expected Time Complexity:** `O(K*Log(N))`  
**Expected Auxiliary Space:** `O(N)` 

### Examples

**Example 1:**   
```
Input:
N = 4
mat[][] =     [[16, 28, 60, 64], [22, 41, 63, 91], [27, 50, 87, 93], [36, 78, 87, 94 ]]
K = 3
Output: 27
Explanation: 27 is the 3rd smallest element.

```

**Example 2:**   
```
Input:
N = 4
mat[][] =     [[10, 20, 30, 40], [15, 25, 35, 45], [24, 29, 37, 48], [32, 33, 39, 50]]
K = 7
Output: 30
Explanation: 30 is the 7th smallest element.
```

### Constraints

+ `1 <= N <= 50`
+ `1<=Mat[i][j]<=10^4`
+ `1<=K<=N*N`

## Solutions

```cpp
class Solution{
    public:
    int kthSmallest(int mat[MAX][MAX], int n, int k){
        //Your code here
        int mi = 0, mx = 1000;
        while(mi < mx){
            int mid = mi + (mx-mi)/2 ;
            int midPos = 0;
            for(int i=0; i< n; i++)
                if(mid >= mat[i][0])
                    midPos += (upper_bound(mat[i], mat[i] + n, mid) - mat[i]);
            if(midPos < k) mi = mid+1;
            else mx = mid;
        }
        return mi;
    }


};
```

