---
layout: post
title: Reach a given score                       
summary:
tags:
    - dynamic-programming
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/reach-a-given-score1418/0/?track=DSASP-DP&batchId=154#)  

Consider a game where a player can score `3` or `5` or `10` points in a move. Given a total score `n`, find the number of distinct combinations to reach the given score.

**Your Task:** 

Complete `count()` function which takes `N` as an argument and returns the number of ways/combinations to reach the given score.


**Expected Time Complexity:** `O(N)`              
**Expected Auxiliary Space:** `O(N)`


### Examples

**Example 1:**   
```
Input:
n = 8
Output: 1
Explanation:when n = 8,{3,5} and {5,3}
are the two possible permutations but
these represent the same combination.
Hence output is 1.
```

**Example 2:**   
```
Input:
n = 20
Output: 4
Explanation:When n = 20, {10,10},
{5,5,5,5},{10,5,5} and {3,3,3,3,3,5}
are different possible permutations.
Hence output will be 4.
```

### Constraints

+ `1 <= N <= 10^3`


## Solutions

```cpp
//Function to find the number of distinct combinations to reach the given score.
ll count(ll m) 
{
    //code here
    ll dp[m+1][4];
    dp[0][0]=dp[0][1]=dp[0][2]=dp[0][3]=1;
    for(int i=1;i<=m;i++){
        dp[i][0] = dp[i][1] = 0;
        if(i>=3) dp[i][1] += dp[i-3][1];
        dp[i][2] = dp[i][1];
        if(i>=5) dp[i][2] += dp[i-5][2];
        dp[i][3] = dp[i][2];
        if(i>=10) dp[i][3] += dp[i-10][3];
    }
    return dp[m][3];
}
```

