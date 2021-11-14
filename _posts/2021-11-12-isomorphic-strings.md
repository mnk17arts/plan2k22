---
layout: post
title: Isomorphic Strings
description: 
summary:
tags:
    - string
    - hashtable
    - leetcode
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/isomorphic-strings)  
Given two strings `s` and `t`, determine if they are isomorphic.

Two strings `s` and `t` are isomorphic if the characters in `s` can be replaced to get `t`.

All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character, but a character may map to itself.

### Examples

**Example 1:**    
```
Input: s = "egg", t = "add"
Output: true
```

**Example 2:**   
```
Input: s = "foo", t = "bar"
Output: false
```

**Example 3:**   
```
Input: s = "paper", t = "title"
Output: true
```

### Constraints
+ `1 <= s.length <= 5 * 10^4`
+ `t.length == s.length`
+ `s` and `t` consist of any valid ascii character.

## Solutions

```cpp
class Solution {
public:
    bool isIsomorphic(string s, string t) {
      map<char,char> mp, np;
      for(int i=0; i<s.size(); i++){
        if(mp.find(s[i]) == mp.end()) mp[s[i]] = t[i];
        else if(mp[s[i]] != t[i]) return false;
        if(np.find(t[i]) == np.end()) np[t[i]] = s[i];
        else if(np[t[i]] != s[i]) return false;
      }
      return true;
    }
};
```
