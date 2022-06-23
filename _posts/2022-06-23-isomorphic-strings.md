---
layout: post
title: Isomorphic Strings  
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/isomorphic-strings-1587115620/0/?track=DSASP-Strings&batchId=154#)  

Given two strings '`str1`' and '`str2`', check if these two strings are isomorphic to each other.
Two strings `str1` and `str2` are called isomorphic if there is a one to one mapping possible for every character of `str1` to every character of `str2` while preserving the order.
Note: All occurrences of every character in `str1` should map to the same character in `str2`


**Your Task:** 
You don't need to read input or print anything.Your task is to complete the function `areIsomorphic()` which takes the string `str1` and string `str2` as input parameter and  check if two strings are isomorphic. The function returns `true` if strings are isomorphic else it returns `false`.


**Expected Time Complexity:** `O(|str1|+|str2|)`  
**Expected Auxiliary Space:** `O(Number of different characters)`

### Examples

**Example 1:**   
```
Input:
str1 = aab
str2 = xxy
Output: 1
Explanation: There are two different
charactersin aab and xxy, i.e a and b
with frequency 2and 1 respectively.
```

**Example 2:**   
```
Input:
str1 = aab
str2 = xyz
Output: 0
Explanation: There are two different
charactersin aab but there are three
different charactersin xyz. So there
won't be one to one mapping between
str1 and str2.
```

### Constraints

+ `1 <= |s1|, |s2|  <= 2*10^4`

## Solutions

```cpp
class Solution{
    public:
    //Function to check if two strings are isomorphic.
    bool areIsomorphic(string str1, string str2)
    {
        
        // Your code here
        int n = str1.size(), m =str2.size();
        if(n!=m) return false;
        unordered_map<char,char> mp,mp2;
        for(int i=0; i<n; i++){
            if(mp.find(str1[i])!=mp.end() && mp[str1[i]]!=str2[i]) return false;
            if(mp2.find(str2[i])!=mp2.end() && mp2[str2[i]]!=str1[i]) return false;
            mp[str1[i]] = str2[i];
            mp2[str2[i]] = str1[i];
        }
        return true;
    }
};
```

