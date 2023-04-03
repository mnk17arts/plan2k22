---
layout: post
title: Remainder on dividing by 11
summary:
tags:
  - geeksforgeeks
  - math
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/aa8c89caad6b5c3a76ba5e6d65454f77aac3f3543526/1)

Given a big positive number x represented as string, find value of x % 11 or x mod 11. Output is expected as an integer.

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function xmod11() which takes string x as the input parameter and returns the integer value of x%11.

**Expected Time Complexity:** `O(length of string x)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**

```
Input: x = 1345
Output: 3
Explanation: 1345 % 11 = 3 
```

**Example 2:**

```
Input: x = 231456786543567898765
Output: 1
Explanation: 231456786543567898765 % 11 = 1
```

### Constraints

- `1 <= n,m ≤ 10^5`
- `1 <= a1[i], a2[i] <= 10^6`

## Solutions

```cpp

class Solution {
  public:
    int xmod11(string x)
    {
        int n = 0;
        for(auto i: x)
            n = ((n * 10) + (i - '0')) % 11;
        
        return n;
    }
};

```
