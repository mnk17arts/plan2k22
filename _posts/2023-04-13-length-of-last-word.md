---
layout: post
title: Length of Last Word
summary:
tags:
  - leetcode
  - string
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/removing-stars-from-a-string/description/)

Given a string s consisting of words and spaces, return the length of the last word in the string.

A word is a maximal substring consisting of non-space characters only.


### Examples

**Example 1:**  

```
Input: s = "Hello World"
Output: 5
Explanation: The last word is "World" with length 5.
```

**Example 2:**  

```
Input: s = "   fly me   to   the moon  "
Output: 4
Explanation: The last word is "moon" with length 4.
```

**Example 3:**  

```
Input: s = "luffy is still joyboy"
Output: 6
Explanation: The last word is "joyboy" with length 6.
```

### Constraints

- `1 <= s.length <= 10^4`
- `s` consists of lowercase English letters and ` `.
- There will be at least one word in `s`.


## Solutions

```cpp

class Solution {
public:
    int lengthOfLastWord(string s) {
        int res = 0;
        while(s.back() == ' ') s.pop_back();
        for(int i = s.length() - 1; i >= 0 && s[i] != ' '; i--, res++){}
        return res;
    }
};

```
