---
layout: post
title: Reverse Words in a String III
description: 
summary: 
tags:
    - pointers
    - string
    - leetcode
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/reverse-words-in-a-string-iii/)
Given a string `s`, reverse the order of characters in each word within a sentence while still preserving whitespace and initial word order.


### Examples
**Example 1:**
```
Input: s = "Let's take LeetCode contest"
Output: "s'teL ekat edoCteeL tsetnoc"
```

**Example 2:**
```
Input: s = "God Ding"
Output: "doG gniD"
```

### Constraints
+ `1 <= s.length <= 5 * 10^4`
+ `s` contains printable **ASCII** characters.
+ `s` does not contain any leading or trailing spaces.
+ There is **at least** one word in `s`.
+ All the words in s are separated by a single space.

## Solutions
```cpp
class Solution {
public:
    string reverseWords(string s) {
        
        s += " ";
        
        int left=0,right,size=s.size(),temp;
        
        char t;
        
        while(left < size){ 
            
            right = left;
            
            while(s[right] != ' ')right++;
            
            temp = right--;
            
            while(left<right){
                t = s[left];
                s[left] = s[right];
                s[right] = t; 
                left++;
                right--;
            }
            
            left = temp + 1;
        }
        
        s.pop_back();
        return s;
    }
};
```
