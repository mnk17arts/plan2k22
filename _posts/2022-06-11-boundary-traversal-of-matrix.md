---
layout: post
title: Boundary traversal of matrix
summary:
tags:
    - matrix
    - geeksforgeeks
    - cpp
    - easy
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/boundary-traversal-of-matrix-1587115620/0/#)  

You are given a matrix of dimensions `n x m`. The task is to perform boundary traversal on the matrix in a clockwise manner.

**Your Task:** 
Complete the function `boundaryTraversal()` that takes `matrix`, `n and m` as input parameters and returns the list of integers that form the boundary traversal of the matrix in a clockwise manner.

**Expected Time Complexity:** `O(N+M)`  
**Expected Auxiliary Space:** `O(1)` 

### Examples

**Example 1:**   
```
Input:
n = 4, m = 4
matrix[][] = [[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12], [13, 14, 15,16]]
Output: 1 2 3 4 8 12 16 15 14 13 9 5
Explanation:
The matrix is:
1 2 3 4
5 6 7 8
9 10 11 12
13 14 15 16
The boundary traversal is:
1 2 3 4 8 12 16 15 14 13 9 5
```

**Example 2:**   
```
Input:
n = 3, m = 4
matrrix[][] = [[12, 11, 10, 9], [8, 7, 6, 5], [4, 3, 2, 1]]
Output: 12 11 10 9 5 1 2 3 4 8
```

### Constraints

+ `1 <= n, m<= 100`
+ `0 <= matrixi <= 1000`

## Solutions

```cpp
class Solution{
    public:
    //Function to return list of integers that form the boundary 
    //traversal of the matrix in a clockwise manner.
    vector<int> boundaryTraversal(vector<vector<int> > matrix, int n, int m) {
        // code here
        if(n==1) return matrix[0];
        vector<int> res;
        for(int i=0; i<m; i++) res.push_back(matrix[0][i]);
        for(int i=1; i<n; i++) res.push_back(matrix[i][m-1]);
        if(m!=1){
            for(int i=m-2; i>=0; i--) res.push_back(matrix[n-1][i]);
            for(int i=n-2; i>0; i--) res.push_back(matrix[i][0]);            
        }

        return res;
        
    }

};
```

