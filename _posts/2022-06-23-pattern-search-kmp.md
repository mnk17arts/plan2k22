---
layout: post
title: Pattern Search KMP    
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - hard
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/pattern-search-kmp/0/?track=DSASP-Strings&batchId=154#)  

Given a string `S` and a pattern `P` of all lowercase characters. The task is to check if the pattern exists in the string or not.

**Your Task:** 
The task is to complete the function `KMPSearch()` which returns `true` or `false` depending on whether pattern is present in the string or not, and `computeLPSArray()` which computes the longest prefix suffix for every index.


**Expected Time Complexity:** `O(N+M)`  
**Expected Auxiliary Space:** `O(M)`

### Examples

**Example 1:**   
```
Input:
S = aabaacaadaabaaba
P = aaaab
Output: No
Explanation: Given pattern is not found
in the given string S.
```

**Example 2:**   
```
Input:
S = aabaacaadaabaaba
P = caada
Output: Yes
Explanation: Given pattern is found in
the given string S.
```

### Constraints

+ `1 ≤ |S| , |P| <= 10^4`

## Solutions

```cpp
class Solution{
    public:
    //Function to fill lps[] for given patttern pat[0..M-1].
    void computeLPSArray(string pat, int M, int* lps) 
    { 
        // Your code here
        int len = 0, start = 1;
        while(start < M){
            if(pat[len]==pat[start]) { len++; lps[start] = len; start++; }
            else {
                if(len!=0) len = lps[len-1];
                else { lps[start]=0; start++; }
            }
        }
    } 

    //Function to check if the pattern exists in the string or not.
    bool KMPSearch(string pat, string txt) 
    {
        // Your code here
        int n=txt.size(),m=pat.size(),i=0,j=0;
        int lps[m]={0};
        computeLPSArray(pat, m, lps);
        while( i<n ){
            if(txt[i]==pat[j]) {i++; j++;}
            if(j==m) return true;
            else if(i<n&&txt[i]!=pat[j]) { 
                if(j!=0) j=lps[j-1];
                else i++;
            }
        }
        return false;
    }
};
```

