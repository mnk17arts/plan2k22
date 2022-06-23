---
layout: post
title: The Modified String    
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - easy
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/the-modified-string-1587115621/0/?)  

Ishaan is playing with strings these days. He has found a new string. He wants to modify it as per the following rules to make it valid:

+ The string should not have three consecutive same characters (Refer example for explanation).
+ He can add any number of characters anywhere in the string.


Find the minimum number of characters which Ishaan must insert in the string to make it valid.

**Your Task:** 
This is a function problem. You only need to complete the function `modified()` that returns the answer.


**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
S = aabbbcc
Output: 1
Explanation: In aabbbcc 3 b's occur
consecutively, we add a 'd',and Hence,
output will be aabbdbcc.
```

**Example 2:**   
```
Input:
S = aaaaa
Output: 2
Explanation:  In aaaaa 5 a's occur
consecutively,we need to add 2 'b', and
Hence, the output will be aababaa.
```

### Constraints

+ `1 <= Length of S <= 10^5`

## Solutions

```cpp
class Solution{
    public:
    //Function to find minimum number of characters which Ishaan must insert  
    //such that string doesn't have three consecutive same characters.
    int modified (string a)
    {
        // Your code here
        int d = 0, res = 0;
        for(int i=1; i<a.size(); i++){
            if(a[i]==a[i-1]){
                if(d==1) {res++; d=0;}
                else d = 1;
            }else d=0;
        }
        return res;
    }
};
```

