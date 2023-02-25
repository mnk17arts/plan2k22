---
layout: post
title: Implement Atoi
summary:
tags:
  - geeksforgeeks
  - string
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/implement-atoi/1)

Your task  is to implement the function atoi. The function takes a string(str) as argument and converts it to an integer and returns it.

Note: You are not allowed to use inbuilt function.

**Your Task:**

Complete the function atoi() which takes a string as input parameter and returns integer value of it. if the input string is not a numerical string then returns -1.

Note: Numerical strings are the string where either every character is in between 0-9 or where the first character is '-' and the rest all characters are in between 0-9.


**Expected Time Complexity:** `O(|S|)`  
**Expected Auxiliary Space:** `O(1)` 

### Examples

**Example 1:**

```
Input:
str = 123
Output: 123
```

**Example 2:**

```
Input:
str = 21a
Output: -1
Explanation: Output is -1 as all
characters are not digit only.
```

### Constraints

- `1 ≤ |S| ≤ 10`

## Solutions

```cpp

class Solution{
  public:
    /*You are required to complete this method */
    int atoi(string str) {
        //Your code here
        int res = 0, i = 0, n = 0;
        if(str.front() == '-') {
            i = 1;
            n = 1;
        }
        for(; i < str.length(); i++) {
            if(!isdigit(str[i])) {
                return -1;
            }
            res *= 10;
            res += (str[i] - '0');
        }
        if(n == 1) {
            res *= -1;
        }
        return res;
    }
};

```
