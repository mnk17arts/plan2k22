---
layout: post
title: Word Pattern
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

## Problem Statement - [*link*](https://leetcode.com/problems/word-pattern)  
Given a pattern and a string `s`, find if `s` follows the same pattern.

Here follow means a full match, such that there is a bijection between a letter in pattern and a non-empty word in `s`.

### Examples

**Example 1:**    
```
Input: pattern = "abba", s = "dog cat cat dog"
Output: true
```

**Example 2:**   
```
Input: pattern = "abba", s = "dog cat cat fish"
Output: false
```

**Example 3:**   
```
Input: pattern = "aaaa", s = "dog cat cat dog"
Output: false
```

**Example 4:**   
```
Input: pattern = "abba", s = "dog dog dog dog"
Output: false
```

### Constraints
+ `1 <= pattern.length <= 300`
+ pattern contains only lower-case English letters.
+ `1 <= s.length <= 3000`
+ `s` contains only lower-case English letters and spaces `' '`.
+ `s` does not contain any leading or trailing spaces.
+ All the words in `s` are separated by a single space.

## Solutions

```cpp
class Solution {
public:
    bool wordPattern(string pattern, string s) {
      vector<string> v;
      stringstream ss(s);
      string x;
      while(ss >> x) v.push_back(x);
      if(pattern.size() == 1 and v.size() == 1) return true;
      else if(pattern.size() != v.size()) return false;
      map<char,string> mp;
      map<string,char> np;
      for(int i=0; i<v.size(); i++){
        if(mp.find(pattern[i]) == mp.end()) mp[pattern[i]] = v[i];
        else if(mp[pattern[i]] != v[i]) return false;
        if(np.find(v[i]) == np.end()) np[v[i]] = pattern[i];
        else if(np[v[i]] != pattern[i]) return false;
      }
      return true;
    }
};
```

