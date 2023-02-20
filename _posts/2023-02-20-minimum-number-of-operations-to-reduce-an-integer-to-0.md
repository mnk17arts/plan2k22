---
layout: post
title: Minimum Operations to Reduce an Integer to 0
summary:
tags:
  - leetcode
  - math
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/minimum-operations-to-reduce-an-integer-to-0/)

You are given a positive integer n, you can do the following operation any number of times:

+ Add or subtract a power of 2 from n.

Return the minimum number of operations to make n equal to 0.

A number x is power of 2 if x == 2i where i >= 0.

### Examples

**Example 1:**
```
Input: n = 39
Output: 3
Explanation: We can do the following operations:
- Add 20 = 1 to n, so now n = 40.
- Subtract 23 = 8 from n, so now n = 32.
- Subtract 25 = 32 from n, so now n = 0.
It can be shown that 3 is the minimum number of operations we need to make n equal to 0.
```

**Example 2:**
```
Input: n = 54
Output: 3
Explanation: We can do the following operations:
- Add 21 = 2 to n, so now n = 56.
- Add 23 = 8 to n, so now n = 64.
- Subtract 26 = 64 from n, so now n = 0.
So the minimum number of operations is 3.
```

### Constraints

- `1 <= n <= 10^5`

## Solutions

```cpp

class Solution {
public:
    bool isPower(int n) {
        int pn = log2(n);
        return n == pow(2, pn); 
    }
    int minOperations(int n) {
        int res = 1;
        while(!isPower(n)) {
            int p = log2(n);
            int left = n - pow(2, p);
            int right = pow(2, p + 1) - n;
            n = min(left, right);
            res++;
        }
        return res;
    }
};

```
