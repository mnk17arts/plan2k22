---
layout: post
title: Reverse a String
summary:
tags:
  - geeksforgeeks
  - string
  - cpp
  - easy
minute: 1+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/reverse-a-string/1)

You are given a string s. You need to reverse the string.

**Your Task:**

You only need to complete the function reverseWord() that takes s as parameter and returns the reversed string.


**Expected Time Complexity:** `O(|S|)`  
**Expected Auxiliary Space:** `O(1)` 

### Examples

**Example 1:**

```
Input:
s = Geeks
Output: skeeG
```

**Example 2:**

```
Input:
s = for
Output: rof
```

### Constraints

- `1 ≤ length of s1 and s2 ≤ 1000`

## Solutions

```cpp

class Solution{
  public:
 string reverseWord(string str){
    
  //Your code here
  int n = str.length();
  for(int i = 0; i < n / 2; i++) {
      swap(str[i], str[n - 1 - i]);
  }
  return str;
}
};

```
