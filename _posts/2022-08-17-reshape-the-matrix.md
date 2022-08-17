---
layout: post
title: Reshape the Matrix                       
summary:
tags:
    - leetcode
    - array
    - cpp
    - easy
minute: 8 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/reshape-the-matrix/)  

In MATLAB, there is a handy function called reshape which can reshape an `m x n` matrix into a new one with a different size `r x c` keeping its original data.

You are given an `m x n` matrix mat and two integers `r` and `c` representing the number of rows and the number of columns of the wanted reshaped matrix.

The reshaped matrix should be filled with all the elements of the original matrix in the same row-traversing order as they were.

If the `reshape` operation with given parameters is possible and legal, output the new reshaped matrix; Otherwise, output the original matrix.


### Examples


**Example 1:**   

<img src="https://assets.leetcode.com/uploads/2021/04/24/reshape1-grid.jpg">

```
Input: mat = [[1,2],[3,4]], r = 1, c = 4
Output: [[1,2,3,4]]
```

**Example 2:**   

<img src="https://assets.leetcode.com/uploads/2021/04/24/reshape2-grid.jpg">

```
Input: mat = [[1,2],[3,4]], r = 2, c = 4
Output: [[1,2],[3,4]]
```

### Constraints

+ `m == mat.length`
+ `n == mat[i].length`
+ `1 <= m, n <= 100`
+ `1 <= r, c <= 300`
+ `-1000 <= mat[i][j] <= 1000`


## Solutions

```cpp
class Solution {
public:
    vector<vector<int>> matrixReshape(vector<vector<int>>& mat, int r, int c) {
        if(mat.size() * mat[0].size() != r*c) return mat;
        vector<vector<int>> res(r,vector<int> (c,0));
        int ri=0,ci=0;
        for(int i=0;i<mat.size();i++){
            for(int j=0;j<mat[0].size();j++){
                res[ri][ci] = mat[i][j];
                ci++;
                if(ci%c==0) { ci=0; ri++;}
            }
        }
        return res;
    }
};
```

