---
layout: post
title: Power of Two
description: 
summary: 
tags:
    - bit-manipulation
    - leetcode
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/power-of-two/)
Given an integer `n`, return *`true` if it is a power of two. Otherwise, return `false`.*

An integer `n` is a power of two, if there exists an integer `x` such that `n == 2^x`.
 

### Examples

**Example 1:**  
```
Input: n = 1
Output: true
Explanation: 20 = 1
```

**Example 2:**  
```
Input: n = 16
Output: true
Explanation: 24 = 16
```

**Example 3:**  
```
Input: n = 3
Output: false
```

**Example 4:**  
```
Input: n = 4
Output: true
```

**Example 5:**  
```
Input: n = 5
Output: false
```

### Constraints
+ `-2^31 <= n <= 2^31 - 1`

**Follow up**: Could you solve it without loops/recursion?

## Solutions

```cpp

class Solution {
public:
    int one(int n){
        int c=0;
        for(unsigned int b = 1; b <= n && b > 0; b<<=1)
            if(n&b) c++;
        return c;
    }
    bool isPowerOfTwo(int n) {
        return n>0 ? one(n)==1 : false;
    }
};

```
