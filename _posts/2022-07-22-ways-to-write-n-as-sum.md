---
layout: post
title: Ways to write n as sum                       
summary:
tags:
    - dynamic-programming
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/ways-to-write-n-as-sum-1587115621/0/?track=DSASP-DP&batchId=154#)  

Given a positive integer `N`, the task is to find the number of different ways in which `N` can be written as a sum of two or more positive integers.

**Your Task:** 

Your task is to complete the function `countWays()` which takes `1` argument(`N`) and returns the answer%(`10^9 + 7`).


**Expected Time Complexity:** `O(N^2)`              
**Expected Auxiliary Space:** `O(N)`


### Examples

**Example 1:**   
```
Input:
N = 5
Output: 6
Explanation: 
1+1+1+1+1
1+1+1+2
1+1+3
1+4
2+1+2
2+3
So, a total of 6 ways.
```

**Example 2:**   
```
Input:
N = 3
Output: 2
```

### Constraints

+ `1 <= N <= 10^3`


## Solutions

```cpp
class Solution
{
    public:
    //Function to count the number of different ways in which n can be 
    //written as a sum of two or more positive integers.
    int countWays(int n)
    {
        // your code here
        int dp[n+1][n];
        for(int i=0;i<n;i++){
            dp[0][i]=1;
            dp[i+1][0]=0;
        }
        for(int i=1;i<n+1;i++)
            for(int j=1;j<n;j++)
                if(i>=j)
                    dp[i][j] = dp[i][j-1] + dp[i-j][j];
                else dp[i][j] = dp[i][j-1];
        return dp[n][n-1];
        
    }
};
```

