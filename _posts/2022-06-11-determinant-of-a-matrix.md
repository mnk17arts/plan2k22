---
layout: post
title: Determinant of a Matrix
summary:
tags:
    - matrix
    - geeksforgeeks
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/determinant-of-a-matrix-1587115620/0/)  

Given a square matrix of size `N x N`. The task is to find the determinant of this matrix.

**Your Task:** 
You don't need to read input or print anything. Complete the function `determinantOfMatrix()` that takes matrix and its size n as input parameters and returns the determinant of the matrix.

**Expected Time Complexity:** `O(N^4)`  
**Expected Auxiliary Space:** `O(N^2)` 

### Examples

**Example 1:**   
```
Input:
N = 4
matrix[][] = [[1, 0, 2, -1], [3, 0, 0, 5], [2, 1, 4, -3], [1, 0, 5, 0]]
Output: 30
Explanation:
Determinant of the given matrix is 30.
```

**Example 2:**   
```
Input:
N = 3
matrix[][] = [[1, 2, 3], [4, 5, 6], [7, 10, 9]]
Output: 12
Explanation:
Determinant of the given matrix is 12.
```

### Constraints

+ `1 <= N <=8`
+ `-10 <= matrix[i][j] <= 10`

## Solutions

```cpp
class Solution{
    public:
    //Function for finding determinant of matrix.
    void gcf(vector<vector<int>> matrix, vector<vector<int>> &cf, int n, int x){
        for(int i=1; i<n; i++){
            int j=0;
            for(int k=0; k<n; k++){
                if(x==k) continue;
                cf[i-1][j++] = matrix[i][k];
            }
        }
    }
    int determinantOfMatrix(vector<vector<int> > matrix, int n){
        // code here 
        if(n==1) return matrix[0][0];
        if(n==2) return (matrix[0][0]*matrix[1][1] - matrix[0][1]*matrix[1][0]);
        
        vector<vector<int>> cf(n-1,vector<int>(n-1));
        int sum = 0, sign = 1;
        for(int i=0; i<n; i++){
            gcf(matrix, cf, n, i);
            sum += sign*matrix[0][i]*determinantOfMatrix(cf, n-1);
            sign *= -1;
        }
        return sum;
    }

};
```

