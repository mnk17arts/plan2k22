---
layout: post
title: Smallest window in a string containing all the characters of another string  
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/smallest-window-in-a-string-containing-all-the-characters-of-another-string-1587115621/0/?#)  

Given two strings `S` and `P`. Find the smallest window in the string `S` consisting of all the characters(including duplicates) of the string `P`.  Return "`-1`" in case there is no such window present. In case there are multiple such windows of same length, return the one with the least starting index. 

**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `smallestWindow()` which takes two string `S` and `P` as input paramters and returns the smallest window in string `S` having all the characters of the string `P`. In case there are multiple such windows of same length, return the one with the least starting index.


**Expected Time Complexity:** `O(|S|)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
S = "timetopractice"
P = "toc"
Output: 
toprac
Explanation: "toprac" is the smallest
substring in which "toc" can be found.
```

**Example 2:**   
```
Input:
S = "zoomlazapzo"
P = "oza"
Output: 
apzo
Explanation: "apzo" is the smallest 
substring in which "oza" can be found.
```

### Constraints

+ `1 ≤ |str|,|patt| ≤ 10^5`

## Solutions

```cpp
class Solution{
    public:
    //Function to find the smallest window in the string s consisting
    //of all the characters of string p.
    string smallestWindow (string s, string p)
    {
        // Your code here
        unordered_map<char, int> um;
        for(int i=0; i<p.size(); i++) um[p[i]]++;
        int pc = um.size();
        int l = 0, r = 0, n = s.size();
        int idx, len = n;
        while(r<n){
            if(um.find(s[r])!=um.end()){
                um[s[r]]--;
                if(um[s[r]]==0) pc--;
            }
            while(pc==0){
                if(len > r-l+1) { len = r-l+1 ; idx = l; }
                if(um.find(s[l])!=um.end()){
                    um[s[l]]++;
                    if(um[s[l]]==1) pc++;
                }
                l++;
            }
            r++;
        }
        return len==n ? "-1" : s.substr(idx, len);
    }
};
```

