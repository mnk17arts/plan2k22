---
layout: post
title: Kth Smallest Number in Multiplication Table
description: 
summary:
tags:
    - binary-search
    - leetcode
    - cpp
    - hard
minute: 5 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/kth-smallest-number-in-multiplication-table)  

Nearly everyone has used the `Multiplication Table`. The multiplication table of size `m x n` is an integer matrix mat where `mat[i][j] == i * j` **(1-indexed)**.

Given three integers `m`, `n`, and `k`, return the `kth` smallest element in the `m x n` multiplication table.

### Examples

**Example 1:**   
<img src="https://assets.leetcode.com/uploads/2021/05/02/multtable1-grid.jpg"> 
```
Input: m = 3, n = 3, k = 5
Output: 3
Explanation: The 5th smallest number is 3.
```

**Example 2:**    
<img src="https://assets.leetcode.com/uploads/2021/05/02/multtable2-grid.jpg">
```
Input: m = 2, n = 3, k = 6
Output: 6
Explanation: The 6th smallest number is 6.
```

### Constraints
+ `1 <= m, n <= 3 * 10^4`
+ `1 <= k <= m * n`

## Solutions

```cpp
class Solution {
public:
    bool enough(int x, int m, int n, int k) {
        int count = 0;
        for (int i = 1; i <= m; i++) {
            count += min(x / i, n);
        }
        return count >= k;
    }
    int findKthNumber(int m, int n, int k) {
        int lo = 1, hi = m * n;
        while (lo < hi) {
            int mi = lo + (hi - lo) / 2;
            if (!enough(mi, m, n, k)) lo = mi + 1;
            else hi = mi;
        }
        return lo;   
    }
};
```

