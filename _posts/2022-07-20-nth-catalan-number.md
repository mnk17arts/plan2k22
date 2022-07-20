---
layout: post
title: Nth catalan number                      
summary:
tags:
    - dynamic-programming
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/nth-catalan-number0817/0/?track=DSASP-DP&batchId=154)  

Given a number `N`. The task is to find the Nth catalan number.
The first few Catalan numbers for `N = 0, 1, 2, 3, …` are `1, 1, 2, 5, 14, 42, 132, 429, 1430, 4862, …`
Note: Positions start from 0 as shown above.

<img src="https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-6e37684751c57a980ebaca5148b4736a_l3.svg">

**Your Task:** 

Complete `findCatalan()` function that takes `n` as an argument and returns the `N`th Catalan number. The output is printed by the driver code.


**Expected Time Complexity:** `O(N)`              
**Expected Auxiliary Space:** `O(N)`



### Examples

**Example 1:**   
```
Input:
N = 5
Output: 42
```

**Example 2:**   
```
Input:
N = 4
Output: 14
```

### Constraints

+ `1 ≤ N <= 100`


## Solutions

```cpp

class Solution
{
    public:
    //Function to find the nth catalan number.
    cpp_int findCatalan(int n) 
    {
        //code here
        cpp_int dp[n+1];
        dp[0]=dp[1]=1;
        for(int i=2;i<=n;i++)
            for(int j=0;j<i;j++)
                dp[i] += dp[j]*dp[i-1-j];
        return dp[n];
    }
};
```

