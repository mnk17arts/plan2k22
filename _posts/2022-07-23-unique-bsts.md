---
layout: post
title: Unique BST's                       
summary:
tags:
    - dynamic-programming
    - geeksforgeeks
    - cpp
    - medium
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/unique-bsts-1587115621/0/?track=DSASP-DP&batchId=154#)  

Given an integer. Find how many structurally unique binary search trees are there that stores the values from 1 to that integer (inclusive). 

**Your Task:** 

You don't need to read input or print anything. Your task is to complete the function `numTrees()` which takes the integer N as input and returns the total number of Binary Search Trees possible with keys [`1.....N`] inclusive. Since the answer can be very large, return the answer modulo `1e9 + 7`.


**Expected Time Complexity:** `O(N^2)`              
**Expected Auxiliary Space:** `O(N)`


### Examples

**Example 1:**   
```
Input:
N = 2
Output: 2
Explanation:for N = 2, there are 2 unique
BSTs
     1               2  
      \            /
       2         1
```

**Example 2:**   
```
Input:
N = 3
Output: 5
Explanation: for N = 3, there are 5
possible BSTs
  1           3     3       2     1
    \        /     /      /  \     \
     3      2     1      1    3     2
    /      /       \                 \
   2      1         2                 3
```

### Constraints

+ `1 <= N <= 10^3`


## Solutions

```cpp
class Solution
{
    public:
    //Function to return the total number of possible unique BST. 
    int numTrees(int N) 
    {
        // Your code here
        long long dp[N+1]={0};
        dp[0]=dp[1]=1;
        int mod = 1e9+7;
        for(int i=2;i<=N;i++)
            for(int j=1;j<=i;j++)
                dp[i] = (dp[i] + ((dp[i-j])%mod*(dp[j-1])%mod)%mod)%mod;
        return dp[N]%mod;
    }
};
```

