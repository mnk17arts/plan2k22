---
layout: post
title: Consecutive Characters
summary:
tags:
    - string
    - leetcode
    - cpp
    - easy
minute: 2 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/consecutive-characters)  

The power of the string is the maximum length of a non-empty substring that contains only one unique character.

Given a string `s`, return *the power of `s`*.

### Examples

**Example 1:**  
```
Input: s = "leetcode"
Output: 2
Explanation: The substring "ee" is of length 2 with the character 'e' only.
```

**Example 2:**  
```
Input: s = "abbcccddddeeeeedcba"
Output: 5
Explanation: The substring "eeeee" is of length 5 with the character 'e' only.
```

**Example 3:**  
```
Input: s = "triplepillooooow"
Output: 5
```

**Example 4:**  
```
Input: s = "hooraaaaaaaaaaay"
Output: 11
```

**Example 5:**  
```
Input: s = "tourist"
Output: 1
```

### Constraints
+ `1 <= s.length <= 500`
+ `s` consists of only lowercase English letters.

## Solutions

```cpp
class Solution {
public:
    int maxPower(string s) {
      int res = 1, t=1;
      for(int i=1; i<s.size(); i++){
        if(s[i-1]==s[i]) t++;
        else t=1;
        res=max(res,t);
      }
      return res;
    }
};
```

