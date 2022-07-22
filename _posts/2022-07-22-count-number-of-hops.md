---
layout: post
title: Count number of hops                       
summary:
tags:
    - dynamic-programming
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/count-number-of-hops-1587115620/0/?track=DSASP-DP&batchId=154#)  

A frog jumps either `1`, `2`, or `3` steps to go to the top. In how many ways can it reach the top. As the answer will be large find the answer modulo `1000000007`.

**Your Task:** 

Your task is to complete the function `countWays()` which takes `1` argument(`N`) and returns the answer%(`10^9 + 7`)


**Expected Time Complexity:** `O(N)`              
**Expected Auxiliary Space:** `O(1)`


### Examples

**Example 1:**   
```
Input:
N = 1
Output: 1
```

**Example 2:**   
```
Input:
N = 4
Output: 7
Explanation:Below are the 7 ways to reach
4
1 step + 1 step + 1 step + 1 step
1 step + 2 step + 1 step
2 step + 1 step + 1 step
1 step + 1 step + 2 step
2 step + 2 step
3 step + 1 step
1 step + 3 step
```

### Constraints

+ `1 <= N <= 10^5`


## Solutions

```cpp
class Solution
{
    public:
    //Function to count the number of ways in which frog can reach the top.
    long long countWays(int n) {   
        // your code here
        if(n<3) return n;
        long long ppp = 1,pp = 2, p = 4, mod=1e9+7;
        for(int i=3;i<n;i++){
            long long temp = p + pp + ppp;
            ppp = pp;
            pp = p;
            p = temp%mod;
        }
        return p;
    }
};
```

