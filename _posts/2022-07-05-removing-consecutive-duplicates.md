---
layout: post
title: Removing consecutive duplicates       
summary:
tags:
    - stack
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/removing-consecutive-duplicates-1587115621/0/?track=DSASP-Stack&batchId=154)  

You are given string `str`. You need to remove the consecutive duplicates from the given string using a Stack.

**Your Task:** 
This is a function problem. You need to complete the function `removeConsecutiveDuplicates()` that takes a string as a parameter and returns the modified string. The printing is done automatically by the driver code.


**Expected Time Complexity:** `O(N)`
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input: 
aaaaaabaabccccccc

Output: 
ababc

Explanation: 
Removing all consecutive duplicates, 
we have no duplicates consecutively.
```


**Example 2:**   
```
Input: 
abbccbcd

Output: 
abcbcd

Explanation: 
Removing all the consecutive duplicates, 
we have the output as abcbcd.
```


### Constraints

+ `1 <= |str| <= 1000`

## Solutions

```cpp
class Solution
{
    public:
    //Function to remove consecutive duplicates from given string using Stack.
    string removeConsecutiveDuplicates(string str)
    {
        // Your code here
        stack<char> s;
        for(char c: str){
            if(!s.empty() && s.top()==c) continue;
            s.push(c);
        }
        string res = "";
        while(!s.empty()) {
            res = s.top() + res;
            s.pop();
        }
        return res;
    }
};
```

