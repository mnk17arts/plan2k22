---
layout: post
title:  Find All Anagrams in a String
description: 
summary: 
tags:
    - string
    - slidingwindow
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/find-all-anagrams-in-a-string/)
Given two strings `s` and `p`, return *an array of all the start indices of `p`'s anagrams in `s`. You may return the answer in **any order**.*

An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.
 
### Examples   
**Example 1:**  
```
Input: s = "cbaebabacd", p = "abc"
Output: [0,6]
Explanation:
The substring with start index = 0 is "cba", which is an anagram of "abc".
The substring with start index = 6 is "bac", which is an anagram of "abc".
```

**Example 2:**  
```
Input: s = "abab", p = "ab"
Output: [0,1,2]
Explanation:
The substring with start index = 0 is "ab", which is an anagram of "ab".
The substring with start index = 1 is "ba", which is an anagram of "ab".
The substring with start index = 2 is "ab", which is an anagram of "ab".
```

### Constraints
+ `1 <= s.length, p.length <= 3 * 10^4`
+ `s` and `p` consist of lowercase English letters.

## Solutions

```cpp
class Solution {
public:
    vector<int> findAnagrams(string s, string p) {
        
        map<char,int> pc,tc;
 
        int psz = p.size();
        vector<int> res;
        
        for(auto c: p) pc[c]++;
        
        for(int i=0; i<psz; i++) tc[s[i]]++;
        
        for(int i=psz; i<s.size(); i++){
            
            if(pc.size() == tc.size())
                if(pc == tc)
                    res.push_back(i-psz);
            
            char c = s[i-psz];
            if(tc[c] == 1) tc.erase(c);
            else tc[c]--;
            tc[s[i]]++;
        }
        
        if(pc.size() == tc.size())
            if(pc == tc)
                res.push_back(s.size()-psz);
        return res;
    }
};

```

