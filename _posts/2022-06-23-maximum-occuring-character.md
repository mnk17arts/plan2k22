---
layout: post
title: Maximum Occuring Character 
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/maximum-occuring-character-1587115620/0/?track=DSASP-Strings&batchId=154#)  

Given a string `str`. The task is to find the maximum occurring character in the string `str`. If more than one character occurs the maximum number of time then print the lexicographically smaller character.

**Your Task:** 
The task is to complete the function `getMaxOccuringChar()` which returns the character which is most occurring.

**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(Number of distinct characters)`

### Examples

**Example 1:**   
```
Input:
str = testsample
Output: e
Explanation: e is the character which
is having the highest frequency.
```

**Example 2:**   
```
Input:
str = output
Output: t
Explanation:  t and u are the characters
with the same frequency, but t is
lexicographically smaller.
```

### Constraints

+ `1 <=|S| ≤ 100`

## Solutions

```cpp
class Solution{
    public:
    //Function to find the maximum occurring character in a string.
    char getMaxOccuringChar(string str)
    {
        // Your code here
        int alp[26] = {0};
        int m = 0;
        for(int i=0; i<str.size(); i++)
            m = max(m, ++alp[str[i]-'a']);

        for(int i=0; i<26; i++)
            if(alp[i]==m)
                return i+'a';
        return 0;
    }
};
```

