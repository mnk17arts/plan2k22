---
layout: post
title: Print Matrix in snake Pattern 
summary:
tags:
    - matrix
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/print-matrix-in-snake-pattern-1587115621/0/?#)  

Given a matrix of size `N x N`. Print the elements of the matrix in the snake like pattern depicted below.
<img src="https://contribute.geeksforgeeks.org/wp-content/uploads/snake-pattern.jpg">


**Your Task:** 
You dont need to read input or print anything. Complete the function `snakePattern()` that takes matrix as input parameter and returns a list of integers in order of the values visited in the snake pattern. 

**Expected Time Complexity:** `O(N*N)`  
**Expected Auxiliary Space:** `O(N*N)` for the resultant list only.  

### Examples

**Example 1:**   
```
Input:
N = 3 
matrix[][] = [[45, 48, 54], [21, 89, 87], [70, 78, 15]]
Output: 45 48 54 87 89 21 70 78 15 
Explanation:
Matrix is as below:
45 48 54
21 89 87
70 78 15
Printing it in snake pattern will lead to 
the output as 45 48 54 87 89 21 70 78 15.
```

**Example 2:**   
```
Input:
N = 2
matrix[][] = [[1, 2], [3, 4]]
Output: 1 2 4 3
Explanation:
Matrix is as below:
1 2 
3 4
Printing it in snake pattern will 
give output as 1 2 4 3.
```

### Constraints

+ `1 <= N <= 100`
+ `1 <= matrix[i][j] <= 100`

## Solutions

```cpp
class Solution{
    public:
    //Function to return list of integers visited in snake pattern in matrix.
    vector<int> snakePattern(vector<vector<int> > matrix)
    {   
        // code here
        int m = matrix.size(), n = matrix[0].size();
        if( m==1 ) return matrix[0];
        vector<int> res;
        for( int i=0; i<m; i++){
            if(i%2==0)
                for(int j=0; j<n; j++)
                    res.push_back(matrix[i][j]);
            else
                for(int j=n-1; j>=0; j--)
                    res.push_back(matrix[i][j]);
        }
        return res;
    }

};
```

