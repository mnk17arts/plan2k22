---
layout: post
title: Ugly Number                       
summary:
tags:
    - leetcode
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/ugly-number/description/)  

An ugly number is a positive integer whose prime factors are limited to 2, 3, and 5.

Given an integer n, return true if n is an ugly number.


### Examples


**Example 1:**   
```
Input: n = 6
Output: true
Explanation: 6 = 2 × 3
```


**Example 2:**   
```
Input: n = 1
Output: true
Explanation: 1 has no prime factors, therefore all of its prime factors are limited to 2, 3, and 5.
```

### Constraints

+ `-2^31 <= n <= 2^31 - 1`

## Solutions

```cpp
class Solution {
public:
    bool isUgly(int n) {
        if(n<=0) return false;
        else if(n==1) return true;
        else {
            while(n%2==0) {
                n/=2;
            }
            while(n%3==0) {
                n/=3;
            }
            while(n%5==0) {
                n/=5;
            }
            if(n==1) 
                return true;
            else 
                return false;
        }
    }
};
```

