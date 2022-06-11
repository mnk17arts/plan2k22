---
layout: post
title: Make Matrix Beautiful
summary:
tags:
    - matrix
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/make-matrix-beautiful-1587115620/0/#)  

A beautiful matrix is a matrix in which the sum of elements in each row and column is equal.
Given a square matrix of size `NxN`. Find the minimum number of operation(s) that are required to make the matrix beautiful. In one operation you can increment the value of any one cell by `1`.
  

**Your Task:** 
You don't need to read input or print anything. Complete the function `findMinOpeartion()` that takes `matrix` and `n` as input parameters and returns the minimum number of operations.

**Expected Time Complexity:** `O(N * N)`   
**Expected Auxiliary Space:** `O(N)`  

### Examples

**Example 1:**   
```
Input:
N = 2
matrix[][] = [[1, 2], [3, 4]]
Output: 4
Explanation:
Updated matrix:
4 3
3 4
1. Increment value of cell(0, 0) by 3
2. Increment value of cell(0, 1) by 1
Hence total 4 operation are required.
```

**Example 2:**   
```
Input:
N = 3
matrix[][] = [[1, 2, 3], [4, 2, 3], [3, 2, 1]]
Output: 6
Explanation:
Original matrix is as follows:
1 2 3
4 2 3
3 2 1
We need to make increment in such a way 
that each row and column has one time 2, 
one time 3 , one time 4. For that we 
need 6 operations.
```

### Constraints

+ `1 <= N <= 100`
+ `1 <= matrix[i][j] <= 200`

## Solutions

```cpp
class Solution{
    public:
    //Function to find minimum number of operations that are required 
    //to make the matrix beautiful.
    int findMinOpeartion(vector<vector<int> > matrix, int n)    {
        // code here 
        int mr = INT_MIN, mc = INT_MIN;
        int sum = 0;
        for(int i=0; i<n; i++){
            int rs = 0, cs = 0;
            for(int j=0; j<n; j++){
                rs += matrix[i][j];
                cs += matrix[j][i];
            }
            sum += rs;
            mr = max(mr, rs);
            mc = max(mc, cs);
        }
        return n*max(mr, mc) - sum;
    } 

};
```

