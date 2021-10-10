---
layout: post
title: Permutation in String
description: 
summary: 
tags:
    - string
    - leetcode
    - cpp
    - medium
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/permutation-in-string/)
Given two strings `s1` and `s2`, return *`true` if `s2` contains a permutation of `s1`, or `false` otherwise.*

In other words, return `true` if one of `s1`'s permutations is the substring of `s2`.

### Examples
**Example 1:**  
```
Input: s1 = "ab", s2 = "eidbaooo"
Output: true
Explanation: s2 contains one permutation of s1 ("ba").
```

**Example 2:**  
```
Input: s1 = "ab", s2 = "eidboaoo"
Output: false
```

### Constraints
+ `1 <= s1.length, s2.length <= 10^4`
+ `s1` and `s`2 consist of lowercase English letters.

## Solutions
```cpp
class Solution {
public:
    bool checkInclusion(string s1, string s2) {
        vector<int> one(26,0), two(26,0);
        for(char i: s1) one[i-'a']++;
        for(int i=0; i<s2.size(); i++){
            if(i>=s1.size()) two[s2[i-s1.size()]-'a']--;
            two[s2[i]-'a']++;
            if(one==two) return true;
        }
        return false;
    }
};
```
