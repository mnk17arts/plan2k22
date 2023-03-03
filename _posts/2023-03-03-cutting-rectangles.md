---
layout: post
title: Cutting Rectangles
summary:
tags:
  - geeksforgeeks
  - math
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/a7a4da81b20f4a05bbd93f5786fcf7478298f4f5/1)

Given a rectangle of dimensions `L x B` find the minimum number (`N`) of identical squares of maximum side that can be cut out from that rectangle so that no residue remains in the rectangle. Also find the dimension `K` of that square.

**Your Task:**

You do not need to read input or print anything. Your task is to complete the function `minimumSquares()` which takes `L` and `B` as input parameters and returns a list of 2 integers containing the values of `N` and `K` respectively.

**Expected Time Complexity:** `O(log min(L, B))`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**

```
Input: L = 2, B = 4
Output: N = 2, K = 2
Explaination: 2 squares of 2x2 dimension.
```

**Example 2:**

```
Input: L = 6, B = 3
Output: N = 2, K = 3
Explaintion: 2 squares of 3x3 dimension. 
```

### Constraints

- `1 ≤ L, B  <= 10^9`

## Solutions

```cpp

class Solution{
    public:
    vector<long long int> minimumSquares(long long int L, long long int B)
    {
        // code here
        long long minSide = __gcd(L, B);
        long long numSqr = (L / minSide) * (B / minSide);
        vector<long long int> res = {numSqr, minSide};
        return res;
    }
};

```
