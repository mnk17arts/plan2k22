---
layout: post
title: Boolean Matrix
summary:
tags:
    - matrix
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/boolean-matrix-problem-1587115620/0/#)  

Given a boolean matrix of size `RxC` where each cell contains either `0` or `1`, modify it such that if a matrix cell `matrix[i][j]` is `1` then all the cells in its `i`th row and `j`th column will become `1`.   

**Your Task:** 
You dont need to read input or print anything. Complete the function `booleanMatrix()` that takes the matrix as input parameter and modifies it in-place.

**Expected Time Complexity:** `O(R * C)` 
**Expected Auxiliary Space:** `O(R + C)`  

### Examples

**Example 1:**   
```
Input:
R = 2, C = 2
matrix[][] = [[1, 0], [0, 0]]
Output: 
1 1
1 0 
Explanation:
Only cell that has 1 is at (0,0) so all 
cells in row 0 are modified to 1 and all 
cells in column 0 are modified to 1.
```

**Example 2:**   
```
Input:
R = 4, C = 3
matrix[][] = [[ 1, 0, 0], [ 1, 0, 0], [ 1, 0, 0], [ 0, 0, 0]]
Output: 
1 1 1
1 1 1
1 1 1
1 0 0 
Explanation:
The position of cells that have 1 in
the original matrix are (0,0), (1,0)
and (2,0). Therefore, all cells in row
0,1,2 are and column 0 are modified to 1. 
```

### Constraints

+ `1 ≤ R, C ≤ 1000`
+ `0 ≤ matrix[i][j] ≤ 1`

## Solutions

```cpp
class Solution{
    public:
    //Function to modify the matrix such that if a matrix cell matrix[i][j]
    //is 1 then all the cells in its ith row and jth column will become 1.
    void booleanMatrix(vector<vector<int> > &matrix)    {
        // code here
        int m = matrix.size(), n = matrix[0].size(); 
        int r[m] = {0} ,c[n] ={0};
        for(int i=0; i<m; i++)
            for(int j=0; j<n; j++)
                if(matrix[i][j]){
                    r[i] = 1;
                    c[j] = 1;
                }
        for(int i=0; i<m; i++)
            for(int j=0; j<n; j++)
                if(r[i] || c[j])
                    matrix[i][j] = 1;
    }

};
```

