---
layout: post
title: Alternating Digit Sum
summary:
tags:
  - leetcode
  - math
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/alternating-digit-sum/description/)

You are given a positive integer n. Each digit of n has a sign according to the following rules:

+ The most significant digit is assigned a positive sign.
+ Each other digit has an opposite sign to its adjacent digits.

Return the sum of all digits with their corresponding sign.


### Examples

**Example 1:**  


```
Input: n = 521
Output: 4
Explanation: (+5) + (-2) + (+1) = 4.
```

**Example 2:**  


```
Input: n = 111
Output: 1
Explanation: (+1) + (-1) + (+1) = 1.
```

**Example 3:**

```
Input: n = 886996
Output: 0
Explanation: (+8) + (-8) + (+6) + (-9) + (+9) + (-6) = 0.
```

### Constraints

- `1 <= n <= 10^9`


## Solutions

```cpp

class Solution {
    public int alternateDigitSum(int n) {
       int sum = 0;
        int sign = 1;
        String str = Integer.toString(n);
        for(char c: str.toCharArray()) {
            sum += (c - '0') * (sign);
            sign *= -1;
        }
        return sum;
    }
}

```
