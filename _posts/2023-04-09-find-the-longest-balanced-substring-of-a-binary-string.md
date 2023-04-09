---
layout: post
title: Find the Longest Balanced Substring of a Binary String
summary:
tags:
  - leetcode
  - string
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/optimal-partition-of-string/description/)

You are given a binary string s consisting only of zeroes and ones.

A substring of s is considered balanced if all zeroes are before ones and the number of zeroes is equal to the number of ones inside the substring. Notice that the empty substring is considered a balanced substring.

Return the length of the longest balanced substring of s.

A substring is a contiguous sequence of characters within a string.


### Examples

**Example 1:**  

```
Input: s = "01000111"
Output: 6
Explanation: The longest balanced substring is "000111", which has length 6.
```

**Example 2:**  

```
Input: s = "00111"
Output: 4
Explanation: The longest balanced substring is "0011", which has length 4. 
```

**Example 3:**  

```
Input: s = "111"
Output: 0
Explanation: There is no balanced substring except the empty substring, so the answer is 0.
```


### Constraints

- `1 <= s.length <= 50`
- `s` consists of only '0' and '1'.


## Solutions

```cpp

class Solution {
public:
    int findTheLongestBalancedSubstring(string s) {
        int maxi = 0;
        for (int i = 0; i < s.size();) {
            int zeros = 0;
            int ones = 0;
            while (i < s.size() and s[i] == '0') {
                zeros++;
                i++;
            }
            while (i < s.size() and s[i] == '1') {
                ones++;
                i++;
            }
            int len = 2 * min(zeros, ones);
            maxi = max(maxi, len);
        }
        return maxi;
    }
};

```
