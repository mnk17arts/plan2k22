---
layout: post
title:  Search a 2D Matrix
description: 
summary: 
tags:
    - string
    - leetcode
    - cpp
    - easy
minute: 2 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/palindrome-number/)
Given an integer `x`, return *`true` if `x` is palindrome integer.*

An integer is a palindrome when it reads the same backward as forward. For example, `121` is palindrome while `123` is not.
 
 
### Examples   
**Example 1:**   
```
Input: x = 121
Output: true
```

**Example 2:**  
```
Input: x = -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
```

**Example 3:**   
```
Input: x = 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.
```

**Example 4:**   
```
Input: x = -101
Output: false
```

### Constraints
+ `-2^31 <= x <= 2^31 - 1`

## Solutions

```cpp

class Solution {
public:
    bool isPalindrome(int x) {
      string s = to_string(x);
      int size = s.size();
      for(int i=0; i<size/2; i++){
        if(s[i]!=s[size-1-i])
          return false;
      }
      return true;
    }
};

```

