---
layout: post
title: Rabin Karp - Pattern Searching    
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/rabin-karp-pattern-searching/0/?track=DSASP-Strings&batchId=154#)  

Given a string `S` and a pattern `P` of lowercase characters. The task is to check if the pattern is present in string or not.

**Your Task:** 
You need to complete the function `search` which takes `3` arguments(`S`, `P` and prime `q`) and returns `true` if the pattern is found else returns `false`.


**Expected Time Complexity:** `O(N+M)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
S = aabaacaadaabaaba
P = aaba
Output: Yes
Explanation: You can find the patter at
starting at index 12.
```

**Example 2:**   
```
Input:
S = aabaacaadaabaaba
P = asdfa
Output: No
Explanation: Pattern doesn't exist in
the given string S.
```

### Constraints

+ `1 ≤ |S| , |P| <= 10^4`

## Solutions

```cpp
class Solution{
    public:
    // d is the number of characters in the input alphabet 
    #define d 256 

    //Function to check if the pattern is present in string or not.
    bool search(string pat, string txt, int q) 
    { 
        // Your code here
        int pl = pat.size(), tl = txt.size();
        int ph = 0, th = 0;
        int dpow = 1;
        for(int i=1; i<pl; i++) dpow = (dpow*d)%q;
        
        for(int i=0; i<pl; i++){
            ph = (ph*d + pat[i])%q;
            th = (th*d + txt[i])%q;
        }
        
        for(int i=0; i<tl-pl+1; i++){
            if(th==ph) {
                int j=0;
                for(; j<pl; j++)
                    if(pat[j]!=txt[i+j])
                    break;
                if(j==pl) return true;
            }
            if(i<tl-pl){
                th = (d*(th - dpow*txt[i]) + txt[i+pl])%q;
                if(th < 0) th+=q;
            }
        }
        return false;
        
    }
};
```

