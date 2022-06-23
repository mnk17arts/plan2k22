---
layout: post
title: Keypad typing   
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/keypad-typing0119/0/?#)  

You are given a string `S` of alphabet characters and the task is to find its matching decimal representation as on the shown keypad. Output the decimal representation corresponding to the string. For ex: if you are given “`amazon`” then its corresponding decimal representation will be `262966`.
<img src="https://contribute.geeksforgeeks.org/wp-content/uploads/Phone.png">

**Your Task:** 
Complete `printNumber()` function that takes string `s` and its length as parameters and returns the corresponding decimal representation of the given string as a string type. The printing is done by the driver code.


**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input:
S = geeksforgeeks
Output: 4335736743357
Explanation:geeksforgeeks is 4335736743357
in decimal when we type it using the given
keypad.
```

**Example 2:**   
```
Input:
S = geeksquiz
Output: 433577849
Explanation: geeksquiz is 433577849 in
decimal when we type it using the given
keypad.
```

### Constraints

+ `1 <=length of String ≤ 100`

## Solutions

```cpp
class Solution{
    public:
    //Function to find matching decimal representation of a string as on the keypad.
    string printNumber(string s, int n) 
    {
        //code here
        string no = "22233344455566677778889999";
        string res = "";
        for(char c: s)
            res += no[c-'a'];
        return res;
    }
};
```

