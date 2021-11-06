---
layout: post
title: Longest Common Prefix
description: 
summary:
tags:
    - string
    - leetcode
    - cpp
    - easy
minute: 1 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/longest-common-prefix/)
Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

### Examples

**Example 1:**    
```
Input: strs = ["flower","flow","flight"]
Output: "fl"
```

**Example 2:**   
```
Input: strs = ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```

### Constraints
+ `1 <= strs.length <= 200`
+ `0 <= strs[i].length <= 200`
+ `strs[i]` consists of only lower-case English letters.

## Solutions

```cpp
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
      string res = "";
      if(strs[0]=="") return "";
      char t;
      for(int j=0; j<strs[0].size(); j++){
        t=strs[0][j];
        for(int i=1; i<strs.size(); i++){
          if(j >= strs[i].size() or t!=strs[i][j])
            return res;
        }       
        res += t;
      }

      return res;
    }
};
```

