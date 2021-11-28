---
layout: post
title: Number Complement
summary:
tags:
    - leetcode
    - cpp
    - easy
minute: 2 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/number-complement)  

The **complement** of an integer is the integer you get when you flip all the `0`'s to `1`'s and all the `1`'s to `0`'s in its binary representation.

+ For example, The integer `5` is `"101"` in binary and its **complement** is `"010"` which is the integer `2`.

Given an integer `n`, return *its complement*.

### Examples

**Example 1:**   
```
Input: num = 5
Output: 2
Explanation: The binary representation of 5 is 101 (no leading zero bits), and its complement is 010. So you need to output 2.
```

**Example 2:**    
```
Input: num = 1
Output: 0
Explanation: The binary representation of 1 is 1 (no leading zero bits), and its complement is 0. So you need to output 0.
```

### Constraints
+ `0 <= n < 2^31`

## Solutions

```cpp
class Solution {
public:
    int findComplement(int n) {
      if(n==0) return 1;
      string b = "";
      while(n){
        b = (n%2==0? "1" : "0") + b;
        n/=2;
      }
      n = stoi(b,0,2);
      return n;
    }
};
```

