---
layout: post
title: Maximum Difference by Remapping a Digit
summary:
tags:
  - leetcode
  - math
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/maximum-difference-by-remapping-a-digit/)

You are given an integer num. You know that Danny Mittal will sneakily remap one of the 10 possible digits (0 to 9) to another digit.

Return the difference between the maximum and minimum values Danny can make by remapping exactly one digit in num.

Notes:

+ When Danny remaps a digit d1 to another digit d2, Danny replaces all occurrences of d1 in num with d2.
+ Danny can remap a digit to itself, in which case num does not change.
+ Danny can remap different digits for obtaining minimum and maximum values respectively.
+ The resulting number after remapping can contain leading zeroes.
+ We mentioned "Danny Mittal" to congratulate him on being in the top 10 in Weekly Contest 326.

### Examples

**Example 1:**
```
Input: num = 11891
Output: 99009
Explanation: 
To achieve the maximum value, Danny can remap the digit 1 to the digit 9 to yield 99899.
To achieve the minimum value, Danny can remap the digit 1 to the digit 0, yielding 890.
The difference between these two numbers is 99009.
```

**Example 2:**
```
Input: num = 90
Output: 99
Explanation:
The maximum value that can be returned by the function is 99 (if 0 is replaced by 9) and the minimum value that can be returned by the function is 0 (if 9 is replaced by 0).
Thus, we return 99.
```

### Constraints

- `1 <= num <= 10^9`

## Solutions

```cpp

class Solution {
public:
    int minMaxDifference(int num) {
        string n = to_string(num), n1,n2;
        n1 = n, n2 = n;
        char c1=n[0],c2=n[0];
        for(char c: n) {
            if(c == '9') {
                continue;
            }
            else {
                c1 = c;
                break;
            }
        }
        for(int i = 0; i < n.length(); i++) {
            if(n1[i] == c1) {
                n1[i] = '9';
            }
            if(n2[i] == c2) {
                n2[i] = '0';
            }
        }
        int min = stoi(n2);
        int max = stoi(n1);
        return max - min;
    }
};

```
