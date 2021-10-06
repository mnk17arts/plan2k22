---
layout: post
title: Reverse String
description: 
summary: 
tags:
    - pointers
    - leetcode
    - cpp
    - easy
minute: 2 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/reverse-string/)
Write a function that reverses a string. The input string is given as an array of characters `s`.


### Examples
**Example 1:**
```
Input: s = ["h","e","l","l","o"]
Output: ["o","l","l","e","h"]
```

**Example 2:**
```
Input: s = ["H","a","n","n","a","h"]
Output: ["h","a","n","n","a","H"]
```

### Constraints
+ `1 <= s.length <= 10^5`
+ `s[i]` is a printable ascii character.

## Solutions
```cpp
class Solution {
public:
    void reverseString(vector<char>& s) {
       // reverse(s.begin(),s.end());
        int l=0,r=s.size()-1;
        for(;l<r;){
            int t = s[l];
            s[l] = s[r];
            s[r] = t;
            l++;
            r--;
        }
    }
};
```
