---
layout: post
title:  Longest Duplicate Substring
description: 
summary: 
tags:
    - string
    - slidingwindow
    - leetcode
    - cpp
    - hard
minute: 5 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/longest-duplicate-substring/)
Given a string `s`, consider all duplicated substrings: (contiguous) substrings of s that occur 2 or more times. The occurrences may overlap.

Return any duplicated substring that has the longest possible length. If `s` does not have a duplicated substring, the answer is `""`.

### Examples

**Example 1:**   
```
Input: s = "banana"
Output: "ana"
```

**Example 2:**  
```
Input: s = "abcd"
Output: ""
```

### Constraints
+ `2 <= s.length <= 3 * 10^4`
+ `s` consists of lowercase English letters.


## Solutions

```cpp
class Solution {
public:
    string longestDupSubstring(string s) {
      unordered_map<char,vector<int>> sw;
      int n = s.size();
      for(int i=0; i<n; i++) sw[s[i]].push_back(i);
      int mx = 0, idx = -1;
      
      for(int i=0; i<n; i++){
        sw[s[i]].erase(sw[s[i]].begin());
        for(int id : sw[s[i]] ){
          int j = 0;
          while( i+j<n and id+j<n and s[i+j]==s[id+j] ) j++;
          if(j > mx){
            mx = j;
            idx = i;
          }
          if(mx == n-1-i) return s.substr(idx,mx);
        }
      }
      
      return mx ? s.substr(idx,mx) : "" ;
    }
};
```

