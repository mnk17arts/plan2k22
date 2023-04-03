---
layout: post
title: Maximize sum
summary:
tags:
  - geeksforgeeks
  - array
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/contest/gfg-weekly-coding-contest-96/problems/)

Given an array A of size N. We have to construct an array B of size N where B[i]=i*A[i] (1 ≤ i ≤ N). Before constructing array B, you have to swap the elements of array A at max N*N times (possibly 0 times). Find the maximum sum of elements possible of array B, after performing such operations.

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function maximumSum() which takes n and A as input parameters and returns the maximum possible sum.

### Examples

**Example 1:**

```
Input :
n = 2
A = 2 1

Output :
5

Explaination :
If we do not swap the elements the sum is 2*1 + 1*2 = 4
But if we swap the sum is 1*1 + 2*2 = 5
```

**Example 2:**

```
Input :
n = 3
A = 1 1 1

Output :
6

Explaination :
The maximum sum possible is 6 after even after swapping any number of times.
```

### Constraints

- `1 ≤ N ≤ 10^5`
- `1 ≤ A[i] ≤ 10^5`

## Solutions

```cpp

class Solution {
  public:
    long long maximumSum(int n, vector<int> &A) {
        // code here
        long long res = 0;
        sort(A.begin(), A.end());
        for(int i = 1; i <= n; i++) {
            res += (long long)i * A[i - 1];
        }
        return res;
    }
};


```
