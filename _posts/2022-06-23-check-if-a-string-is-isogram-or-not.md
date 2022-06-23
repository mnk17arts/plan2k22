---
layout: post
title: Check if a string is Isogram or not   
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/check-if-a-string-is-isogram-or-not-1587115620/0/)  

Given a string `S` of lowercase alphabets, check if it is isogram or not. An Isogram is a string in which no letter occurs more than once.


**Your Task:** 
This is a function problem. You only need to complete the function `isIsogram()` that takes a string as a parameter and returns either `true` or `false`.


**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(Number of distinct characters)`

### Examples

**Example 1:**   
```
Input:
S = machine
Output: 1
Explanation: machine is an isogram
as no letter has appeared twice. Hence
we print 1.
```

**Example 2:**   
```
Input:
S = geeks
Output: 0
Explanation: geeks is not an isogram
as 'e' appears twice. Hence we print 0.
```

### Constraints

+ `1 <= |s1|, |s2|  <= 10^3`

## Solutions

```cpp
class Solution{
    public:
    //Function to check if a string is Isogram or not.
    bool isIsogram(string s)
    {
        //Your code here
        unordered_set<char> us;
        for(char c: s){
            if(us.find(c)!=us.end()) return false;
            us.insert(c);
        }
        return true;
    }
};
```

