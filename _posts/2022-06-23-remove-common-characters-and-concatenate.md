---
layout: post
title: Remove common characters and concatenate 
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/remove-common-characters-and-concatenate-1587115621/0/?)  

Given two strings `s1` and `s2`. Modify both the strings such that all the common characters of `s1` and `s2` are to be removed and the uncommon characters of `s1` and `s2` are to be concatenated.
Note: If all characters are removed print `-1`.

**Your Task:** 
The task is to complete the function `concatenatedString()` which removes the common characters, concatenates, and returns the string. If all characters are removed then return `-1`.

**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(Number of distinct characters)`

### Examples

**Example 1:**   
```
Input:
s1 = aacdb
s2 = gafd
Output: cbgf
Explanation: The common characters of s1
and s2 are: a, d. The uncommon characters
of s1 and s2 are c, b, g and f. Thus the
modified string with uncommon characters
concatenated is cbgf.
```

**Example 2:**   
```
Input:
s1 = abcs
s2 = cxzca
Output: bsxz
Explanation: The common characters of s1
and s2 are: a,c. The uncommon characters
of s1 and s2 are b,s,x and z. Thus the
modified string with uncommon characters
concatenated is bsxz.
```

### Constraints

+ `1 <=|Length of Strings| ≤ 10000`

## Solutions

```cpp
class Solution{
    public:
    //Function to remove common characters and concatenate two strings.
    string concatenatedString(string s1, string s2) 
    { 
        // Your code here
        unordered_set<char> us1(s1.begin(), s1.end()), us2(s2.begin(), s2.end());
        string res = "";
        for(int i=0; i<s1.size(); i++)
            if(us2.find(s1[i])==us2.end()) res+=s1[i];
        for(int i=0; i<s2.size(); i++)
            if(us1.find(s2[i])==us1.end()) res+=s2[i];
        return res == "" ? "-1" : res;
        
    }
};
```

