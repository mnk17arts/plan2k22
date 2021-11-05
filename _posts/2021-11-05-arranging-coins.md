---
layout: post
title: Arranging Coins
description: 
summary:
tags:
    - binary-search
    - leetcode
    - cpp
    - easy
minute: 1 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/arranging-coins/)
You have `n` coins and you want to build a staircase with these coins. The staircase consists of `k` rows where the `i`th row has exactly `i` coins. The last row of the staircase may be incomplete.

Given the integer `n`, return *the number of complete rows of the staircase you will build.*

### Examples

**Example 1:**    
<img src="https://assets.leetcode.com/uploads/2021/04/09/arrangecoins1-grid.jpg">
```
Input: n = 5
Output: 2
Explanation: Because the 3rd row is incomplete, we return 2.
```

**Example 2:**   
<img src="https://assets.leetcode.com/uploads/2021/04/09/arrangecoins2-grid.jpg">
```
Input: n = 8
Output: 3
Explanation: Because the 4th row is incomplete, we return 3.
```

### Constraints
+ `1 <= n <= 2^31 - 1`

## Solutions

```cpp
class Solution {
public:
    int arrangeCoins(int n) {
      return int(sqrt(2*(long)n+0.25)-0.5);
    }
};
```

