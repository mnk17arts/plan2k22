---
layout: post
title: Longest Substring Without Repeating Characters
description: 
summary: 
tags:
    - string
    - slidingwindow
    - hashtable
    - leetcode
    - cpp
    - medium
minute: 5 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
Given a string `s`, find the length of the longest substring without repeating characters.

### Examples
**Example 1:**  
```
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
```

**Example 2:**  
```
Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

**Example 3:**  
```
Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

**Example 4:**  
```
Input: s = ""
Output: 0
```

### Constraints
+ `0 <= s.length <= 5 * 10^4`
+ `s` consists of English letters, digits, symbols and spaces..

## Solutions
```cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
      
        if(s.size() <= 1) return s.size();
      
        unordered_map<char,int> mnk;
      
        int cur=0,mx=0,left=0,right=0,i=0;
      
        for(;i<s.size();i++){
          
            if(mnk.count(s[i])==0) mnk.insert({s[i],i});
          
            else {
              
              if(mnk[s[i]]>=left)
              left=mnk[s[i]]+1;
              mnk[s[i]]=i;
              
            }
            			
            right=i;
			      cur=right-left+1;
            mx = max(mx,cur);
        }
      
        return mx;
      
    }
};
```
