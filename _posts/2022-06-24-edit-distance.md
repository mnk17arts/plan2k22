---
layout: post
title: Edit Distance    
summary:
tags:
    - string
    - dynamic-programming
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/edit-distance3702/1#)  

Given two strings `s` and `t`. Return the minimum number of operations required to convert `s` to `t`.

The possible operations are permitted:

1. Insert a character at any position of the string.
1. Remove any character from the string.
1. Replace any character from the string with any other character.

**Your Task:** 
You don't need to read or print anything. Your task is to complete the function `editDistance()` which takes strings s and t as input parameters and returns the minimum number of operation to convert the string `s` to string `t`.



**Expected Time Complexity:** `O(|s|*|t|)` 
**Expected Auxiliary Space:** `O(|s|*|t|)`

### Examples

**Example 1:**   
```
Input: 
s = "geek", t = "gesek"
Output: 1
Explanation: One operation is required 
inserting 's' between two 'e's of str1.
```

**Example 2:**   
```
Input : 
s = "gfg", t = "gfg"
Output: 
0
Explanation: Both strings are same.
```

### Constraints

+ `1 <= length of strings <= 100`

## Solutions

```cpp
class Solution{
    public:
    int editDistance(string s, string t) {
        // Code here
        int n=s.size(),m=t.size();
        int dp[n+1][m+1];
        for(int i=0;i<n+1;i++) dp[i][0]=i;
        for(int i=1;i<m+1;i++) dp[0][i]=i;
        for(int i=1;i<n+1;i++)
            for(int j=1;j<m+1;j++)
                if(s[i-1]==t[j-1]) dp[i][j]=dp[i-1][j-1];
                else dp[i][j]=min(dp[i-1][j-1],min(dp[i-1][j],dp[i][j-1]))+1;
        return dp[n][m];
    }
};
```

