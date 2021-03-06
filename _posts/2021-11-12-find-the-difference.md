---
layout: post
title: Find the Difference
description: 
summary:
tags:
    - string
    - hashtable
    - sorting
    - leetcode
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/find-the-difference)  
You are given two strings `s` and `t`.

String `t` is generated by random shuffling string `s` and then add one more letter at a random position.

Return *the letter that was added to `t`.*

### Examples

**Example 1:**    
```
Input: s = "abcd", t = "abcde"
Output: "e"
Explanation: 'e' is the letter that was added.
```

**Example 2:**   
```
Input: s = "", t = "y"
Output: "y"
```

**Example 3:**   
```
Input: s = "a", t = "aa"
Output: "a"
```

**Example 4:**   
```
Input: s = "ae", t = "aea"
Output: "a"
```

### Constraints
+ `0 <= s.length <= 1000`
+ `t.length == s.length + 1`
+ `s` and `t` consist of lower-case English letters.

## Solutions

```cpp
class Solution {
public:
    char findTheDifference(string a, string b) {
      sort(a.begin(), a.end());
      sort(b.begin(), b.end());
      for(int i=0; i<a.size(); i++)
        if(a[i] != b[i]) return b[i];
      return b.back();
    }
};
```

