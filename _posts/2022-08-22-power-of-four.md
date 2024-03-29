---
layout: post
title: Power of Four                       
summary:
tags:
    - leetcode
    - bit-manipulation
    - recursion
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/power-of-four/)  

Given an integer `n`, return true if it is a power of four. Otherwise, return `false`.

An integer `n` is a power of four, if there exists an integer `x` such that `n == 4^x`.


### Examples


**Example 1:**   
```
Input: n = 16
Output: true
```

**Example 2:**   
```
Input: n = 5
Output: false
```

**Example 3:**   
```
Input: n = 1
Output: true
```

### Constraints

+ `-2^31 <= n <= 2^31 - 1`

## Solutions

```cpp
class Solution {
public:
    bool isPowerOfFour(int n) {
        if(!n) return false;
        while(1){
           if(n==1||n==4) return true;
           if(n%4!=0) return false;
           n/=4;
        } 
        return true;
    }
};
```

