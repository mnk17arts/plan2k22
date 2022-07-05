---
layout: post
title: Removing consecutive duplicates - 2       
summary:
tags:
    - stack
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/removing-consecutive-duplicates-2-1587115621/0/?track=DSASP-Stack&batchId=154)  

You are given string `str`. You need to remove the pair of duplicates.
**Note**: The pair should be of adjacent elements and after removing a pair the remaining string is joined together.

**Your Task:** 
This is a function problem. You only need to complete the function `removePair()` that takes a string as a parameter and returns the modified string. Return an empty string if the whole string is deleted.


**Expected Time Complexity:** `O(N)`
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input:
aaabbaaccd

Output: 
ad

Explanation: 
Remove (aa)abbaaccd =>abbaaccd
Remove a(bb)aaccd => aaaccd
Remove (aa)accd => accd
Remove a(cc)d => ad
```


**Example 2:**   
```
Input: 
aaaa

Output: 
Empty String

Explanation: 
Remove (aa)aa => aa
Again removing pair of duplicates then (aa) 
will be removed and we will get 'Empty String'.
```


### Constraints

+ `1 <= |str| <= 1000`

## Solutions

```cpp
class Solution
{
    public:
    //Function to remove pair of duplicates from given string using Stack.
    string removePair(string str)
    {
        // Your code here
        stack<char> s;
        for(char c: str){
            if(!s.empty() && s.top()==c){
                s.pop();
                continue;
            }
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

