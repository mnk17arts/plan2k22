---
layout: post
title: Add Digits
summary:
tags:
    - leetcode
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/add-digits)  

Given an integer `num`, repeatedly add all its digits until the result has only one digit, and return it.

### Examples

**Example 1:**  
```
Input: num = 38
Output: 2
Explanation: The process is
38 --> 3 + 8 --> 11
11 --> 1 + 1 --> 2 
Since 2 has only one digit, return it.
```

**Example 2:**  
```
Input: num = 0
Output: 0
```

### Constraints

+ `0 <= num <= 2^31 - 1`

## Solutions

```cpp
class Solution {
public:
    int addDigits(int num) {
      return num == 0 ? 0 : 1 + (num - 1) % 9;
    }
};
```


```cpp
class Solution {
public:
    int addDigits(int num) {
        int digitalRoot = 0;
        while (num > 0) {
            digitalRoot += num % 10;
            num = num / 10;
            
            if (num == 0 && digitalRoot > 9) {
                num = digitalRoot;
                digitalRoot = 0;  
            }    
        }     
        return digitalRoot;
    }
};
```
