---
layout: post
title:  Egg Dropping Puzzle                         
summary:
tags:
    - dynamic-programming
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/egg-dropping-puzzle-1587115620/0/?track=DSASP-DP&batchId=154#)  

You are given `N` identical eggs and you have access to a K-floored building from `1` to `K`.

There exists a floor `f` where `0 <= f <= K` such that any egg dropped at a floor higher than `f` will break, and any egg dropped at or below floor `f` will not break. There are few rules given below. 

+ An egg that survives a fall can be used again.
+ A broken egg must be discarded.
+ The effect of a fall is the same for all eggs.
+ If the egg doesn't break at a certain floor, it will not break at any floor below.
+ If the eggs breaks at a certain floor, it will break at any floor above.

Return the minimum number of moves that you need to determine with certainty what the value of `f` is.

For more description on this problem see [wiki](http://en.wikipedia.org/wiki/Dynamic_programming#Egg_dropping_puzzle) page

**Your Task:** 

Complete the function `eggDrop()` which takes two positive integer `N` and `K` as input parameters and returns the minimum number of attempts you need in order to find the critical floor.




**Expected Time Complexity:** `O(N*(K^2))`                
**Expected Auxiliary Space:** `O(N*K)` 


### Examples

**Example 1:**   
```
Input:
N = 1, K = 2
Output: 2
Explanation: 
1. Drop the egg from floor 1. If it 
   breaks, we know that f = 0.
2. Otherwise, drop the egg from floor 2.
   If it breaks, we know that f = 1.
3. If it does not break, then we know f = 2.
4. Hence, we need at minimum 2 moves to
   determine with certainty what the value of f is.
```

**Example 2:**   
```
Input:
N = 2, K = 10
Output: 4
```

### Constraints

+ `1 <= N <= 200`
+ `1 <= K <= 200`


## Solutions

```cpp
class Solution
{
    public:
    //Function to find minimum number of attempts needed in 
    //order to find the critical floor.
    int eggDrop(int n, int k) 
    {
        // your code here
        if(k==0) return 0;
        if(n==1) return k;
        int dp[n+1][k+1];
        for(int i=1;i<=n;i++)
            {dp[i][0]=0; dp[i][1]=1;}
        for(int i=1;i<=k;i++)
            dp[1][i] = i;
        for(int i=2;i<=n;i++)
            for(int j=2;j<=k;j++){
                dp[i][j] = INT_MAX;
                for(int k=1;k<=j;k++)
                    dp[i][j] = min(dp[i][j], max(dp[i-1][k-1],dp[i][j-k])+1);
            }
        return dp[n][k];
    }
};
```
