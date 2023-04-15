---
layout: post
title: Valid Palindrome
summary:
tags:
  - leetcode
  - string
  - 2pointers
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/valid-palindrome/description/)

A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string s, return true if it is a palindrome, or false otherwise.


### Examples

**Example 1:**  

```
Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.
```

**Example 2:**  

```
Input: s = "race a car"
Output: false
Explanation: "raceacar" is not a palindrome.
```

**Example 3:**  

```
Input: s = " "
Output: true
Explanation: s is an empty string "" after removing non-alphanumeric characters.
Since an empty string reads the same forward and backward, it is a palindrome.
```

### Constraints

- `1 <= s.length <= 10^5`
- `s` consists only of printable ASCII characters.


## Solutions

```cpp

class Solution {
public:
    bool isPalindrome(string s) {
       string res = "";
       for(char c: s) {
           if(isalpha(c) || isdigit(c)) {
               res += tolower(c);
           }
       } 
       int n = res.length();
       for(int i = 0; i < n / 2; i++) {
           if(res[i] != res[n - 1 - i]) {
               return false;
           }
       }
       return true;
    }
};

```
