---
layout: post
title: Minimum indexed character  
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/minimum-indexed-character-1587115620/0/?)  

Given a string `str` and another string `patt`. Find the minimum index of the character in `str` that is also present in `patt`.

**Your Task:** 
You only need to complete the function `minIndexChar()` that returns the index of answer in `str` or returns `-1` in case no character of `patt` is present in `str`.


**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(Number of distinct characters)`

### Examples

**Example 1:**   
```
Input:
str = geeksforgeeks
patt = set
Output: 1
Explanation: e is the character which is
present in given str "geeksforgeeks"
and is also presen in patt "set". Minimum
index of e is 1. 
```

**Example 2:**   
```
Input:
str = adcffaet
patt = onkl
Output: -1
Explanation: There are none of the
characters which is common in patt
and str.
```

### Constraints

+ `1 ≤ |str|,|patt| ≤ 10^5`
+ `'a' <= stri, patti <= 'z'`

## Solutions

```cpp
class Solution{
    public:
    //Function to find the minimum indexed character.
    int minIndexChar(string str, string patt)
    {
        // Your code here
        for(int i=0; i<str.size(); i++)
            if(patt.find(str[i])!=-1) return i;
        return -1;
    }
};
```

