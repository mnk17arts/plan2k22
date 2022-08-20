---
layout: post
title: Longest Palindromic Substring                       
summary:
tags:
    - leetcode
    - dynamic-programming
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/longest-palindromic-substring/)  

Given a string s, return the longest palindromic substring in s.


### Examples


**Example 1:**   
```
Input: s = "babad"
Output: "bab"
Explanation: "aba" is also a valid answer.
```

**Example 2:**   
```
Input: s = "cbbd"
Output: "bb"
```

### Constraints

+ `1 <= s.length <= 1000`
+ `s consists of only lowercase English letters.`

## Solutions

```cpp
class Solution {
public:
    string longestPalindrome(string s) {
        int j,st=0,en=0;
        for(int i=0;i<s.length();i++){
            j = 1;
            while(i-j>=0&&i+j<s.length()){
                if(s[i-j]!=s[i+j]) break;
                if((2*j)+1 >= en-st+1) {
                    st = i-j;
                    en = i+j;
                }
                j++;
            }
            j = 0;
            while(i-j>=0&&i+j+1<s.length()){
                if(s[i-j]!=s[i+j+1]) break;
                if((2*j)+2 >= en-st+1) {
                    st = i-j;
                    en = i+j+1;
                }
                j++;
            }
        }
        return s.substr(st,en-st+1);
    }
};
```

