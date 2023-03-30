---
layout: post
title: Minimum Integer
summary:
tags:
  - geeksforgeeks
  - array
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/1ccf56f107bcb24242469ea45c02f852165a2184/1)

You are given an array A of size N. Let us denote S as the sum of all integers present in the array. Among all integers present in the array, find the minimum integer X such that S ≤ N*X.

**Your Task:**

The task is to complete the function minimumInteger() which takes an integer N and an integer array A as input parameters and returns the minimum integer which satisfies the condition.

**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**

```
Input:
N = 3,
A = { 1, 3, 2}
Output:
2
Explanation:
Sum of integers in the array is 6.
since 6 ≤ 3*2, therefore 2 is the answer.
```

**Example 2:**

```
Input:
N = 1,
A = { 3 }
Output:
3
Explanation:
3 is the only possible answer
```

### Constraints

- `1 ≤  N ≤ 10^5`
- `1 ≤ A[i] ≤ 10^9`

## Solutions

```cpp

class Solution{
  public:
    int minimumInteger(int N, vector<int> &A) {
        // code here
        long long  sum=0;
        for(int i=0;i<N;sum+=A[i++]);
        int m=INT_MAX;
        for(int i=0;i<N;i++)
            if(sum<=(N*1LL*A[i]))
                    m=min(m,A[i]);        
        return m;
    }
};

```
