---
layout: post
title: Find the Index of the First Occurrence in a String                       
summary:
tags:
    - leetcode
    - string
    - 2pointers
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/description/)  

Given two strings needle and haystack, return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.


### Examples


**Example 1:**   
```
Input: haystack = "sadbutsad", needle = "sad"
Output: 0
Explanation: "sad" occurs at index 0 and 6.
The first occurrence is at index 0, so we return 0.
```


**Example 2:**   
```
Input: haystack = "leetcode", needle = "leeto"
Output: -1
Explanation: "leeto" did not occur in "leetcode", so we return -1.
```

### Constraints

+ `1 <= haystack.length, needle.length <= 10^4`
+ `haystack` and `needle` consist of only lowercase English characters.

## Solutions

```cpp
class Solution {
public:
    int strStr(string haystack, string needle) {
        int res=-1;
        int ns=needle.size(),hs=haystack.size();
        if(ns>hs) return res;
        for(int i=0;i<=hs-ns;i++){
            if(haystack[i]==needle[0]){
                int j=1;
                for(;j<ns;j++){
                    if(haystack[i+j]!=needle[j]){
                        break;
                    }
                }
                if(j==ns){
                    res = i;
                    return res;
                }
            }
        }
        return res;
    }
};
```

