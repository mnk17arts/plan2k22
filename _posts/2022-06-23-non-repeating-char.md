---
layout: post
title: Non Repeating Character    
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/non-repeating-character-1587115620/0/)  

Given a string `S` consisting of lowercase Latin Letters. Return the first non-repeating character in `S`. If there is no non-repeating character, return '`$`'.

**Your Task:** 
You only need to complete the function `nonrepeatingCharacter()` that takes string `S` as a parameter and returns the character. If there is no non-repeating character then return '`$`' .

**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(Number of distinct characters)`

### Examples

**Example 1:**   
```
Input:
S = hello
Output: h
Explanation: In the given string, the
first character which is non-repeating
is h, as it appears first and there is
no other 'h' in the string.

```

**Example 2:**   
```
Input:
S = zxvczbtxyzvy
Output: c
Explanation: In the given string, 'c' is
the character which is non-repeating. 
```

### Constraints

+ `1 <=|S| ≤ 1000`

## Solutions

```cpp
class Solution{
    public:
    //Function to find the first non-repeating character in a string.
    char nonrepeatingCharacter(string s)
    {
       //Your code here
        unordered_map<char, int> um;
        for(char c: s) um[c]++;
        for(int i=0; i<s.size(); i++)
            if(um[s[i]]==1) return s[i];
        return '$';
    }
};
```

