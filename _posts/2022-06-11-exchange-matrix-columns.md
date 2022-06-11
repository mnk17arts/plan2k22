---
layout: post
title: Exchange matrix columns
summary:
tags:
    - matrix
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/exchange-matrix-columns-1587115620/0/)  

You are given a matrix of dimensions (`n1 x m1`). You have to exchange its first column with the last column.

**Your Task:** 
You don't need to take input or print anything. Complete the function `exchangeColumns()` that takes the matrix as input parameter and modifies it in place by exchanging its first column with its last column.

**Expected Time Complexity:** `O(n*m)`  
**Expected Auxiliary Space:** `O(1)` 

### Examples

**Example 1:**   
```
Input:
n1 = 4, m1 = 4
matrix[][] = {{1, 2, 3, 4},
              {5, 6, 7, 8},
              {9, 10, 11, 12},
              {13, 14, 15,16}}
Output: 
4 2 3 1 8 6 7 5 12 10 11 9 16 14 15 13
Explanation:
Matrix is as follow:
1 2 3 4
5 6 7 8
9 10 11 12
13 14 15 16
After exchanging first column with 
last column, we have matrix as follows:
4 2 3 1
8 6 7 5
12 10 11 9
16 14 15 13
```

**Example 2:**   
```
Input:
n1 = 2, m1 = 3
matrix[][] = {{4, 3, 2},
              {1, 5, 6}}
Output: 2 3 4 6 5 1
Explanation:
Matrix is as follows:
4 3 2
1 5 6
After exchanging columns matrix will be:
2 3 4
6 5 1
```

### Constraints

+ `1 <= n, m<= 100`
+ `0 <= matrixi <= 100`

## Solutions

```cpp
class Solution{
    public:
    //Function to exchange first column of a matrix with its last column.
    void exchangeColumns(vector<vector<int> > &matrix){
        // code here
        int n = matrix.size(), m = matrix[0].size();
        for(int i=0 ; i<n; i++)
                swap( matrix[i][0], matrix[i][m-1] );
    }

};
```

