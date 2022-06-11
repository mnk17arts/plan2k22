---
layout: post
title: Sorted matrix  
summary:
tags:
    - matrix
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/sorted-matrix2333/1#)  

Given an `NxN` matrix Mat. Sort all elements of the matrix.
 

**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `sortedMatrix()` which takes the integer `N` and the matrix `Mat` as input parameters and returns the sorted matrix.

**Expected Time Complexity:** `O(N^2 * LogN)`  
**Expected Auxiliary Space:** `O(N^2)` 

### Examples

**Example 1:**   
```
Input:
N=4
Mat=[[10,20,30,40],
[15,25,35,45] 
[27,29,37,48] 
[32,33,39,50]]
Output:
10 15 20 25 
27 29 30 32
33 35 37 39
40 45 48 50
Explanation:
Sorting the matrix gives this result.

```

**Example 2:**   
```
Input:
N=3
Mat=[[1,5,3],[2,8,7],[4,6,9]]
Output:
1 2 3 
4 5 6
7 8 9
Explanation:
Sorting the matrix gives this result.
```

### Constraints

+ `1<=N<=1000`
+ `1<=Mat[i][j]<=10^5`

## Solutions

```cpp
class Solution{
    public:
    vector<vector<int>> sortedMatrix(int N, vector<vector<int>> Mat) {
        // code here
        int arr[N*N];
        int k = 0;
        for(int i=0; i<N; i++)
            for(int j=0; j<N; j++)
                arr[k++] = Mat[i][j];
        sort(arr, arr + N*N);
        k = 0;
        for(int i=0; i<N; i++)
            for(int j=0; j<N; j++)
                Mat[i][j] = arr[k++];
        return Mat;
    }

};
```

