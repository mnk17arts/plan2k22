---
layout: post
title: Rotate by 90 degree
summary:
tags:
    - matrix
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/rotate-by-90-degree-1587115621/0/#)  

Given a square matrix of size `N x N`. The task is to rotate it by `90` degrees in anti-clockwise direction without using any extra space. 
 

**Your Task:** 
You dont need to read input or print anything. Complete the function `rotateby90()` which takes the matrix as input parameter and rotates it by `90` degrees in anti-clockwise direction without using any extra space. You have to modify the input matrix in-place.  

**Expected Time Complexity:** `O(N*N)`  
**Expected Auxiliary Space:** `O(1)` 

### Examples

**Example 1:**   
```
Input:
N = 3 
matrix[][] = {{1, 2, 3},
              {4, 5, 6}
              {7, 8, 9}}
Output: 
Rotated Matrix:
3 6 9
2 5 8
1 4 7
```

**Example 2:**   
```
Input:
N = 2
matrix[][] = {{1, 2},
              {3, 4}}
Output: 
Rotated Matrix:
2 4
1 3
```

### Constraints

+ `1 <= N <= 100`
+ `1 <= matrix[i][j] <= 1000`

## Solutions

```cpp
class Solution{
    public:
    //Function to rotate matrix anticlockwise by 90 degrees.
    void rotateby90(vector<vector<int> >& matrix, int n) 
    { 
        // code here 
        for(int i=0; i<n; i++)
            for(int j=i+1; j<n; j++)
                swap(matrix[i][j], matrix[j][i]);
        for(int i=0; i<n/2; i++)
            for(int j=0; j<n; j++)
                swap(matrix[i][j], matrix[n-1-i][j]);
    } 

};
```

