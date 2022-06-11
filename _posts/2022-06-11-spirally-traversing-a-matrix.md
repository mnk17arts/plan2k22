---
layout: post
title: Spirally traversing a matrix 
summary:
tags:
    - matrix
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/spirally-traversing-a-matrix-1587115621/0/?track=DSASP-Matrix&batchId=154#)  

Given a matrix of size `r*c`. Traverse the matrix in spiral form.  

**Your Task:** 
You dont need to read input or print anything. Complete the function `spirallyTraverse()` that takes `matrix`, `r` and `c` as input parameters and returns a list of integers denoting the spiral traversal of matrix. 

**Expected Time Complexity:** `O(r*c)`  
**Expected Auxiliary Space:** `O(r*c)` for the resultant list only.

### Examples

**Example 1:**   
```
Input:
r = 4, c = 4
matrix[][] = {{1, 2, 3, 4},
           {5, 6, 7, 8},
           {9, 10, 11, 12},
           {13, 14, 15,16}}
Output: 
1 2 3 4 8 12 16 15 14 13 9 5 6 7 11 10
Explanation:
```
<img src="https://www.geeksforgeeks.org/wp-content/uploads/spiral-matrix.png">


**Example 2:**   
```
Input:
r = 3, c = 4  
matrix[][] = {{1, 2, 3, 4},
           {5, 6, 7, 8},
           {9, 10, 11, 12}}
Output: 
1 2 3 4 8 12 11 10 9 5 6 7
Explanation:
Applying same technique as shown above, 
output for the 2nd testcase will be 
1 2 3 4 8 12 11 10 9 5 6 7.
```

### Constraints

+ `1 <= r,c <= 100`
+ `0 <= matrixi <= 100`

## Solutions

```cpp
class Solution{
    public:
    //Function to return a list of integers denoting spiral traversal of matrix.
    vector<int> spirallyTraverse(vector<vector<int> > matrix, int r, int c) {
        // code here
        if(r==1) return matrix[0];
        int top = 0 , right = c-1, bottom = r-1, left = 0;
        vector<int> res;
        while( top <= bottom && left <= right ){
            for( int i = left; i <= right; i++ ) res.push_back(matrix[top][i]);
            top++;
            for( int i = top; i <= bottom; i++) res.push_back(matrix[i][right]);
            right--;
            if(top <= bottom){
                for( int i = right; i >= left; i--) res.push_back(matrix[bottom][i]);
                bottom--;                
            }
            if( left <= right){
                for( int i = bottom; i >= top; i--) res.push_back(matrix[i][left]);
                left++;                
            }

        }
        return res;
    }

};
```

