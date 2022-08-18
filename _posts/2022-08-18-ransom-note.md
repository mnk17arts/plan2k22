---
layout: post
title: Ransom Note                       
summary:
tags:
    - leetcode
    - hash
    - string
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/ransom-note/)  

Given two strings ransomNote and magazine, return true if ransomNote can be constructed by using the letters from magazine and false otherwise.

Each letter in magazine can only be used once in ransomNote.


### Examples


**Example 1:**   
```
Input: ransomNote = "a", magazine = "b"
Output: false
```

**Example 2:**   
```
Input: ransomNote = "aa", magazine = "ab"
Output: false
```

**Example 3:**   
```
Input: ransomNote = "aa", magazine = "aab"
Output: true
```

### Constraints

+ `1 <= ransomNote.length, magazine.length <= 10^5`
+ `ransomNote and magazine consist of lowercase English letters.`


## Solutions

```cpp
class Solution {
public:
    bool canConstruct(string ransomNote, string magazine) {
        int a[26]={0};
        for(char c: magazine) a[c-'a']++;
        for(char c: ransomNote){
            a[c-'a']--;
            if(a[c-'a']<0)
                return false;
        }
        return true;
    }
};
```

