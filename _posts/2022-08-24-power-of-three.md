---
layout: post
title: Power of Three                       
summary:
tags:
    - leetcode
    - recursion
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/power-of-three/)  

Given an integer `n`, return true if it is a power of three. Otherwise, return `false`.

An integer `n` is a power of three, if there exists an integer `x` such that `n == 3^x`.


### Examples


**Example 1:**   
```
Input: n = 27
Output: true
```

**Example 2:**   
```
Input: n = 0
Output: false
```

**Example 3:**   
```
Input: n = 9
Output: true
```

### Constraints

+ `-2^31 <= n <= 2^31 - 1`

## Solutions

```cpp
class Solution {
public:
    bool isPowerOfThree(int n) {
        if(!n) return false;
        while(1){
           if(n==1||n==3) return true;
           if(n%3!=0) return false;
           n/=3;
        } 
        return true;
    }
};
```

