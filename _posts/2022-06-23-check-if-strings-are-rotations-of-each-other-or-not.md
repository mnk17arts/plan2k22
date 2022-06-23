---
layout: post
title: Check if strings are rotations of each other or not     
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/check-if-strings-are-rotations-of-each-other-or-not-1587115620/0/?track=DSASP-Strings&batchId=154)  

Given two strings `s1` and `s2`. The task is to check if `s2` is a rotated version of the string `s1`. The characters in the strings are in lowercase.


**Your Task:** 
The task is to complete the function `areRotations()` which checks if the two strings are rotations of each other. The function returns `true` if string `1` can be obtained by rotating string `2`, else it returns `false`.


**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input:
geeksforgeeks
forgeeksgeeks
Output: 
1
Explanation: s1 is geeksforgeeks, s2 is
forgeeksgeeks. Clearly, s2 is a rotated
version of s1 as s2 can be obtained by
left-rotating s1 by 5 units.
```

**Example 2:**   
```
Input:
mightandmagic
andmagicmigth
Output: 
0
Explanation: Here with any amount of
rotation s2 can't be obtained by s1.
```

### Constraints

+ `1 <= |s1|, |s2|  <= 10^7`

## Solutions

```cpp
class Solution{
    public:
    //Function to check if two strings are rotations of each other or not.
    bool areRotations(string s1,string s2)
    {
        // Your code here
        if(s1.size()!=s2.size()) return false;
        return (s1+s1).find(s2)!=-1 ? true:false;
    }
};
```

