---
layout: post
title: Median in a row-wise sorted Matrix 
summary:
tags:
    - matrix
    - binary-search
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/median-in-a-row-wise-sorted-matrix1527/1#)  

Given a row wise sorted matrix of size `RxC` where `R` and `C` are always odd, find the median of the matrix.
 

**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `median()` which takes the integers `R` and `C` along with the `2D` matrix as input parameters and returns the median of the matrix.

**Expected Time Complexity:** `O(32 * R * log(C))`  
**Expected Auxiliary Space:** `O(1)` 

### Examples

**Example 1:**   
```
Input:
R = 3, C = 3
M = [[1, 3, 5], 
     [2, 6, 9], 
     [3, 6, 9]]

Output: 5

Explanation:
Sorting matrix elements gives us 
{1,2,3,3,5,6,6,9,9}. Hence, 5 is median. 
```

**Example 2:**   
```
Input:
R = 3, C = 1
M = [[1], [2], [3]]
Output: 2
```

### Constraints

+ `1<= R,C <=150`
+ `1<= matrix[i][j] <=2000`

## Solutions

```cpp
class Solution{
    public:
    int median(vector<vector<int>> &matrix, int r, int c){
        // code here   
        int mi = matrix[0][0], mx = matrix[0][c-1];
        for(int i=1; i<r; i++){
            mi = min(mi, matrix[i][0]);
            mx = max(mx, matrix[i][c-1]);
        }
        int medianPos = (r*c)/2 ;
        while( mi < mx){
            int mid = mi + (mx-mi)/2 ;
            int midPos = 0;
            for(int i=0; i<r; i++)
                if( matrix[i][0] <= mid )
                    midPos += upper_bound(matrix[i].begin(), matrix[i].end(), mid) - matrix[i].begin() ;
            if(midPos > medianPos) mx = mid;
            else mi = mid + 1;
        }
        return mi;
    }

};
```

