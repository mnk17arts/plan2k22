---
layout: post
title: Valid Parentheses
summary:
tags:
    - string
    - stack
    - leetcode
    - cpp
    - easy  
minute: 5 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/valid-parentheses)  

Given a string s containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

+ Open brackets must be closed by the same type of brackets.
+ Open brackets must be closed in the correct order.

### Examples
**Example 1:**  
```
Input: s = "()"
Output: true
```

**Example 2:**  
```
Input: s = "()[]{}"
Output: true
```

**Example 3:**  
```
Input: s = "(]"
Output: false
```

### Constraints

+ `1 <= s.length <= 10^4`
+ `s` consists of parentheses only '`()[]{}`'.

## Solutions

```cpp
class Solution {
public:
    bool isValid(string s) {
     stack<char> st;
     for(int i=0; i<s.length(); i++){
       if(s[i]=='{' or s[i]=='[' or s[i]=='(')
         st.push(s[i]);
       else{
         if(st.empty()) return false;
         if(s[i]=='}' and st.top()!='{')
           return false;
         if(s[i]==']' and st.top()!='[')
           return false;
         if(s[i]==')' and st.top()!='(')
           return false;
         st.pop();
       }
     }
      
      if(st.empty()) return true;
      return false;
    }
};
```