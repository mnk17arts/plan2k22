---
layout: post
title: Reverse Integer
description: 
summary: 
tags:
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/reverse-integer/)
Given a signed 32-bit integer `x`, return `x` *with its digits reversed*. If reversing `x` causes the value to go outside the signed 32-bit integer range `[-231, 231 - 1]`, then return `0`.

**Assume the environment does not allow you to store 64-bit integers (signed or unsigned).**

### Examples

**Example 1:**   
```
Input: x = 123
Output: 321
```

**Example 2:**  
```
Input: x = -123
Output: -321
```

**Example 3:**  
```
Input: x = 120
Output: 21
```
**Example 4:**  
```
Input: x = 0
Output: 0
```

### Constraints
+ `-2^31 <= x <= 2^31 - 1`

## Solutions

```cpp

class Solution {
public:
    int reverse(int x) {
        long res = 0;
        while(x){
            res = res*10 + x%10;
            x/=10;
        }
        if(res < INT_MIN or res > INT_MAX)
            return 0;
        else
            return (int)res;
    }
};

```

