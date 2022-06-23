---
layout: post
title: Repeating Character - First Appearance Leftmost   
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/repeating-character-first-appearance-leftmost/0/?track=DSASP-Strings&batchId=154)  

You are given a string `S` (both uppercase and lowercase characters). You need to print the repeated character whose first appearance is leftmost.

**Your Task:** 
This is a function problem. You only need to complete the function `repeatedCharacter()` that takes a string as a parameter and returns the index of the character. If no character repeats then return `-1`.


**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(Number of distinct characters)`

### Examples

**Example 1:**   
```
Input:
S = geeksforgeeks
Output: g
Explanation: We see that both e and g
repeat as we move from left to right.
But the leftmost is g so we print g.

```

**Example 2:**   
```
Input:
S = abcd
Output: -1
Explanation: No character repeats so
we print -1.
```

### Constraints

+ `1 <=|S| ≤ 100`

## Solutions

```cpp
class Solution{
    public:
    //Function to find repeated character whose first appearance is leftmost.
    int repeatedCharacter (string s) 
    { 
        //Your code here
        unordered_map<char, int> um;
        for(char c: s) um[c]++;
        for(int i=0; i<s.size(); i++)
            if(um[s[i]]>1) return i;
        return -1;
    } 
};
```

