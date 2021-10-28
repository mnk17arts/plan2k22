---
layout: post
title: Number of Unique Paths
description: 
summary: 
tags:
    - dynamic-programming
    - gfg
    - cpp
    - easy
minute: 2 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/number-of-unique-paths5339/1#)
Given a `A X B` matrix with your initial position at the top-left cell, find the number of possible unique paths to reach the bottom-right cell of the matrix from the initial position.

**Note:** Possible moves can be either **down** or **right** at any point in time, i.e., we can move to `matrix[i+1][j]` or `matrix[i][j+1]` from `matrix[i][j]`.

### Examples

**Example 1:**   
```
Input:
A = 2, B = 2
Output: 2
Explanation: There are only two unique
paths to reach the end of the matrix of
size two from the starting cell of the
matrix.
```

**Example 2:**  
```
Input:
A = 3, B = 4
Output: 10
Explanation: There are only 10 unique
paths to reach the end of the matrix of
size two from the starting cell of the
matrix.
```


### Your Task:

Complete `NumberOfPath()` function which takes 2 arguments`(A and B)` and returns *the number of unique paths from top-left to the bottom-right cell.*

Expected Time Complexity: `O(A*B)`.
Expected Auxiliary Space: `O(A*B)`.

### Constraints
+ `1 ≤ A ≤ 15`
+ `1 ≤ B ≤ 15`


## Solutions

```cpp
// { Driver Code Starts
//Initial template for C++
#include<bits/stdc++.h>
using namespace std;

 // } Driver Code Ends
//User function template in C++

class Solution
{
    public:
    //Function to find total number of unique paths.
    int NumberOfPath(int a, int b)
    {
        int dp[a][b];
        for(int i=0;i<b;i++) dp[0][i] = 1;
        for(int i=0;i<a;i++) dp[i][0] = 1;
        for(int i=1;i<a;i++)
        for(int j=1;j<b;j++)
        dp[i][j] = dp[i][j-1]+dp[i-1][j];
        return dp[a-1][b-1];
        //code here
    }
};


// { Driver Code Starts.
int main()
{
    //taking total testcases
    int t;
    cin>>t;
    while(t--)
    {
        //taking dimensions of the matrix
        int a,b;
        cin>>a>>b;
        Solution ob;
        //calling NumberOfPath() function
        cout << ob.NumberOfPath(a,b) << endl;
    }
}

  // } Driver Code Ends

```

