---
layout: post
title: Sum of all substrings of a number                       
summary:
tags:
    - dynamic-programming
    - string
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/sum-of-all-substrings-of-a-number-1587115621/0/?track=DSASP-DP&batchId=154#)  

Given an integer `S` represented as a string, the task is to get the sum of all possible sub-strings of this string.
As the answer will be large, print it modulo `10^9+7`. 

**Your Task:** 

You only need to complete the function `sumSubstrings` that takes `S` as an argument and returns the answer modulo `1000000007`.


**Expected Time Complexity:** `O(N)`              
**Expected Auxiliary Space:** `O(N)`


### Examples

**Example 1:**   
```
Input:
S = 1234
Output: 1670
Explanation: Sum = 1 + 2 + 3 + 4 + 12 +
23 + 34 + 123 + 234 + 1234 = 1670
```

**Example 2:**   
```
Input:
S = 421
Output: 491
Explanation: Sum = 4 + 2 + 1 + 42 + 21
```

### Constraints

+ `1 <= |S| <= 10^4`


## Solutions

```cpp
class Solution
{
    public:
    //Function to find sum of all possible substrings of the given string.
    long long sumSubstrings(string s){
        
        // your code here
        int n = s.length();
        long long dp[n];
        dp[0]=s[0]-'0';
        long long sum = dp[0], mod = 1e9+7;
        for(int i=1;i<n;i++){
            dp[i] = ( (i+1)*(s[i]-'0') + 10*dp[i-1] )%mod;
            sum += dp[i];
            sum %= mod;
        }
        return sum;
    }
};
```

