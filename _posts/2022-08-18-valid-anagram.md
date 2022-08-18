---
layout: post
title: Valid Anagram                       
summary:
tags:
    - leetcode
    - hash
    - string
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/valid-anagram/)  

Given two strings s and t, return true if t is an anagram of s, and false otherwise.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.


### Examples


**Example 1:**   
```
Input: s = "anagram", t = "nagaram"
Output: true
```

**Example 2:**   
```
Input: s = "rat", t = "car"
Output: false
```

### Constraints

+ `1 <= s.length, t.length <= 5 * 10^4`
+ `s and t consist of lowercase English letters.`


## Solutions

```cpp
class Solution {
public:
    bool isAnagram(string s, string t) {
        if(s.length()!=t.length()) return false;
        int a[26]={0};
        for(int i=0;i<s.length();i++){
            a[s[i]-'a']++;
            a[t[i]-'a']--;
        }
        for(int i=0;i<26;i++)
            if(a[i]!=0)
                return false;
        return true;
    }
};
```

