---
layout: post
title: Longest Common Subsequence                       
summary:
tags:
    - dynamic-programming
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/longest-common-subsequence-1587115620/0/?track=DSASP-DP&batchId=154)  

Given two sequences, find the length of longest subsequence present in both of them. Both the strings are of uppercase. 

**Your Task:** 

Complete the function `lcs()` which takes the length of two strings respectively and two strings as input parameters and returns the length of the longest subsequence present in both of them.


**Expected Time Complexity:** `O(|str1|*|str2|)`                
**Expected Auxiliary Space:** `O(|str1|*|str2|)`


### Examples

**Example 1:**   
```
Input:
A = 6, B = 6
str1 = ABCDGH
str2 = AEDFHR
Output: 3
Explanation: LCS for input Sequences
“ABCDGH” and “AEDFHR” is “ADH” of
length 3.
```

**Example 2:**   
```
Input:
A = 3, B = 2
str1 = ABC
str2 = AC
Output: 2
Explanation: LCS of "ABC" and "AC" is
"AC" of length 2.
```

### Constraints

+ `1<=size(str1),size(str2)<=10^3`


## Solutions

```cpp
class Solution
{
    public:
    //Function to find the length of longest common subsequence in two strings.
    int lcs(int m, int n, string X, string Y)
    {
        // your code here
        int dp[m+1][n+1];
        for(int i=0;i<=m;i++)
            for(int j=0;j<=n;j++)
                if(i==0||j==0) dp[i][j]=0;
                else if(X[i-1]==Y[j-1]) dp[i][j] = 1 + dp[i-1][j-1];
                else dp[i][j] = max(dp[i-1][j], dp[i][j-1]);
        return dp[m][n];
    }
};
```

