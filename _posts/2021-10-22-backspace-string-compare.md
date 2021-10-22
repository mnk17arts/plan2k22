---
layout: post
title:  Backspace String Compare
description: 
summary: 
tags:
    - string
    - leetcode
    - cpp
    - easy
minute: 2 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/backspace-string-compare/)
Given two strings `s` and `t`, return *`true` if they are equal when both are typed into empty text editors. '`#`' means a backspace character.*

**Note** that after backspacing an empty text, the text will continue empty.
 
### Examples   
**Example 1:**  
```
Input: s = "ab#c", t = "ad#c"
Output: true
Explanation: Both s and t become "ac".
```

**Example 2:**  
```
Input: s = "ab##", t = "c#d#"
Output: true
Explanation: Both s and t become "".
```

**Example 3:**  
```
Input: s = "a##c", t = "#a#c"
Output: true
Explanation: Both s and t become "c".
```

**Example 4:**  
```
Input: s = "a#c", t = "b"
Output: false
Explanation: s becomes "c" while t becomes "b".
```

### Constraints
+ `1 <= s.length, t.length <= 200`
+ `s` and `t` only contain lowercase letters and '`#`' characters.

**Follow up:** Can you solve it in `O(n)` time and `O(1)` space?

## Solutions

```cpp
class Solution {
public:
    bool backspaceCompare(string s, string t) {
        
        int i = s.size()-1, j = t.size()-1;
        int preChar = 0, preChar2 = 0;
        
        while(i >=0 or j>= 0){
            
            while(i >= 0){
                if(s[i] == '#'){
                    preChar++;
                    i--;
                }else if(preChar > 0){
                    preChar--;
                    i--;
                }else{
                    break;
                }
            }            
            
            while(j >= 0){
                
                if(t[j] == '#'){
                    preChar2++;
                    j--;
                }else if(preChar2 > 0){
                    preChar2--;
                    j--;
                }else{
                    break;
                }
            }
            
            if( i>=0 and j>=0 and s[i] != t[j])
                return false;
            
            if(( i>=0 ) != ( j>=0 )) return false;
            
            i--;
            j--;
            
        }
        return true;

    }
};
```

