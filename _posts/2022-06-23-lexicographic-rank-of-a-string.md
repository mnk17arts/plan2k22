---
layout: post
title: Lexicographic Rank Of A String    
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/rank-the-permutations-1587115621/0/?track=DSASP-Strings&batchId=154#)  

You are given a string `S` of lowercase characters, find the `rank` of the string amongst its permutations when sorted lexicographically. Return `0` if the characters are repeated in the string.
Note: Return the `rank%1000000007` as the answer as rank might overflow.

**Your Task:** 
You only need to complete the function `findRank` that takes string `S` as a parameter and returns the rank.


**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input:
S = abc
Output: 1
Explanation: In 'abc' when we sort all the
permutations in lexicographic order 'abc'
will be at the first position.
```

**Example 2:**   
```
Input:
S = acb
Output: 2
Explanation: In 'acb' .The
lexicographically sorted permutations
with letters 'a', 'c', and 'b' will be
at second position. 
```

### Constraints

+ `1 ≤ |S| ≤ 26`

## Solutions

```cpp
class Solution{
    public:
    //Function to find lexicographic rank of a string.
    long long mod = 1e9+7;
    int findRank(string S) 
    {
        //Your code here
        int chars[256] = {0};
        for(int i=0; i<S.size(); i++)
            if(++chars[S[i]] > 1)     return 0;
        
        int n = S.size();
        long fact[27] = {0};
        fact[0] = 1;
        for(int i=1;i<=26;i++){
           fact[i] = (fact[i-1]*i)%mod;
         }

        for(int i=1; i<256; i++) chars[i] += chars[i-1];
        long res = 1;
        for(int i=0; i<n-1; i++){
            long temp = (chars[S[i]-1] * fact[n-1-i]) % mod;
            res = (res + temp)%mod ;
            for(int j=S[i]; j<256; j++) chars[j]--;
        }
        return res%mod;
        
    }
};
```

