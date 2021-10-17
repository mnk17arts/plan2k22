---
layout: post
title:  Search a 2D Matrix
description: 
summary: 
tags:
    - array
    - matrix
    - binary-search
    - leetcode
    - cpp
    - medium
minute: 5 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/search-a-2d-matrix/)
Write an efficient algorithm that searches for a value in an `m x n` matrix. This matrix has the following properties:

+ Integers in each row are sorted from left to right.
+ The first integer of each row is greater than the last integer of the previous row.
 
 
### Examples

**Example 1:**   
<img src="https://assets.leetcode.com/uploads/2020/10/05/mat.jpg">
```
Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3
Output: true
```

**Example 2:**  
<img src="https://assets.leetcode.com/uploads/2020/10/05/mat2.jpg"> 
```
Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 13
Output: false
```

### Constraints
+ `m == matrix.length`
+ `n == matrix[i].length`
+ `1 <= m, n <= 100`
+ `-10^4 <= matrix[i][j], target <= 10^4`

## Solutions

```cpp

class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
      
      int rows = matrix.size();
      int cols = matrix[0].size();
      int l = 0;
      int r = rows*cols - 1;
      
      while(l<=r){
        
        int mid = (l+r)>>1;
        int midr = mid/cols;
        int midc = mid%cols;
        
        if(matrix[midr][midc]==target) return true;
        else if(matrix[midr][midc]>target) r=mid-1;
        else l=mid+1;
        
      }
      
      return false;
    }
};

```

