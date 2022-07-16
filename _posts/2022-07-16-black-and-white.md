---
layout: post
title: Black and White                   
summary:
tags:
    - backtracking
    - geeksforgeeks
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/black-and-white-1587115620/0/?track=DSASP-Backtracking&batchId=154#)  

Given the chessboard dimensions. Find out the number of ways we can place a black and a white Knight on this chessboard such that they cannot attack each other.

Note:
The knights have to be placed on different squares. A knight can move two squares horizontally and one square vertically (L shaped), or two squares vertically and one square horizontally (L shaped). The knights attack each other if one can reach the other in one move. 

**Your Task:** 
Your task is to complete the function `numOfWays()` which takes the chessboard dimensions `N` and `M` as inputs and returns the number of ways we can place `2` Knights on this chessboard such that they cannot attack each other. Since this number can be very large, return it modulo `10^9+7`.


**Expected Time Complexity:** `O(N*M)`           
**Expected Auxiliary Space:** `O(1)`


### Examples

**Example 1:**   
```
Input:
N = 2, M = 2
Output: 12 
```

**Example 2:**   
```
Input:
N = 2, M = 3
Output: 26
```

### Constraints

+ `1 ≤ N * M ≤ 10^5`

## Solutions

```cpp
int n,m;
bool isValid(int i,int j){
    return !(i<0||i>=n||j<0||j>=m); 
}

//Function to find out the number of ways we can place a black and a 
//white Knight on this chessboard such that they cannot attack each other.
long long numOfWays(int N, int M) {
    // write code here
    n=N,m=M;
    int d[9] = { -2, 1, 2, -1, 2, 1, -2, -1, -2  };
    long long int res=0,sols,mod=1e9+7;
    for(int i=0;i<N;i++)
        for(int j=0;j<M;j++){
            sols = N*M-1;
            for(int k=0;k<8;k++)
                if(isValid(i+d[k],j+d[k+1]))
                    sols--;
            res = (res+sols)%mod;
        }
    
    return res;
}
```

