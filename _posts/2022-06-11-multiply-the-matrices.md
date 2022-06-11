---
layout: post
title: Multiply the matrices
summary:
tags:
    - matrix
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/multiply-the-matrices-1587115620/0/)  

When dealing with matrices, you may, sooner or later, run into the elusive task of matrix multiplication. Here, we will try to multiply two matrices and hope to understand the process.

Two matrices `A[][]` and `B[][]` can only be multiplied if number of columns in `A` is equal to number of rows in `B`. The dimensions of the resultant matrix will have `A`'s row size and `B`'s column size.

Given two matrices A and B having (`n1 x m1`) and (`n2 x m2`) dimensions respectively. Multiply `A` and `B`. 

**Your Task:** 
You dont need to read input or print anything. Complete the function `multiplyMatrix()` that takes `A` and `B` as input parameters and returns a matrix containing their product. If the multiplication is not possible return an empty matrix.

**Expected Time Complexity:** `O(N1 * M1 * M2)`  
**Expected Auxiliary Space:** `O(N1 * M2)` 

### Examples

**Example 1:**   
```
Input:
n1 = 3, m1 = 2
A[][] = {{4, 8},
         {0, 2}
         {1, 6}}
n2 = 2, m2 = 2
B[][] = {{5, 2},
         {9, 4}}
Output: 92 40 18 8 59 26
Explanation:
Matrices are of size 3 x 2 and 2 x 2 which 
results in 3 x 2 matrix with elements as:
res[][] = {{92, 40},
           {18, 8}
           {59, 26}}
```

**Example 2:**   
```
Input:
n1 = 1, m1 = 1
A[][] = {2}
n2 = 1, m2 = 1
B[][] = {3}
Output: 6
Explanation: Both matrices are of size 1 x 1 
which results in 1 x 1 matrix having element 6.
```

### Constraints

+ `1 <= n1, m1, n2, m2 <= 30`
+ `0 <= Ai, Bi <= 100`

## Solutions

```cpp
class Solution{
    public:
    //Function to multiply two matrices.
    vector<vector<int> > multiplyMatrix( const vector<vector<int> >& A, const vector<vector<int> >& B)
    {
        // code here
        int r1 = A.size(), c1 = A[0].size();
        int r2 = B.size(), c2 = B[0].size();
        vector<vector<int>> res;
        if( c1 != r2 ) return res;
        for(int i=0; i<r1; i++){
            vector<int> temp;
            for(int j=0; j<c2; j++){
                int sum = 0;
                for(int k=0; k<c1; k++)
                    sum += A[i][k]*B[k][j];
                temp.push_back(sum);
            }
            res.push_back(temp);
        }
        return res;
    }

};
```

