---
layout: post
title: Check if string is rotated by two places     
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/check-if-string-is-rotated-by-two-places-1587115620/0/)  

Given two strings `a` and `b`. The task is to find if the string '`b`' can be obtained by rotating another string '`a`' by exactly `2` places.


**Your Task:** 
The task is to complete the function `isRotated()` which takes two strings as input parameters and checks if given strings can be formed by rotations. The function returns `true` if string `1` can be obtained by rotating string `2` by two places, else it returns `false`.


**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input:
a = amazon
b = azonam
Output: 1
Explanation: amazon can be rotated anti
clockwise by two places, which will make
it as azonam.
```

**Example 2:**   
```
Input:
a = geeksforgeeks
b = geeksgeeksfor
Output: 0
Explanation: If we rotate geeksforgeeks by
two place in any direction , we won't get
geeksgeeksfor.
```

### Constraints

+ `1 <= |a|, |b| <= 10^5`

## Solutions

```cpp
class Solution{
    public:
    //Function to check if a string can be obtained by rotating
    //another string by exactly 2 places.
    bool isRotated(string str1, string str2)
    {
        // Your code here
        int n = str1.size(), m = str2.size();
        if(n!=m) return false;
        string temp=str1, temp2=str1;
        for(int i=0; i<n; i++){
            temp[i] = str1[(i+2)%n];  
            temp2[(i+2)%n] = str1[i];
        }
        return temp==str2 || temp2==str2;    
    }
};
```

