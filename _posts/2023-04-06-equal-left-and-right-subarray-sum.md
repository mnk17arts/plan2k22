---
layout: post
title: Equal Left and Right Subarray Sum
summary:
tags:
  - geeksforgeeks
  - prefix-sum
  - array
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/78a6854c8a2915e05f236aa407dfaa1bbc8ae7d3/1)

Given an array A of n positive numbers. The task is to find the first index in the array such that the sum of elements before it is equal to the sum of elements after it.

Note:  Array is 1-based indexed.

**Your Task:**

The task is to complete the function equalSum() which takes the array and n as input parameters and returns the point. Return -1 if no such point exists.

**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**

```
Input: 
n = 5 
A[] = {1,3,5,2,2} 
Output: 3 
Explanation: For second test case 
at position 3 elements before it 
(1+3) = elements after it (2+2). 
```

**Example 2:**

```
Input:
n = 1
A[] = {1}
Output: 1
Explanation:
Since its the only element hence
it is the only point.
```

### Constraints

- `1 <= n ≤ 10^6`
- `1 <= A[i] <= 10^8`

## Solutions

```cpp

class Solution {
  public:
    int equalSum(int N, vector<int> &A) {
        // code here
        int next = accumulate(A.begin(), A.end(), 0);
        int prev = 0;
        for(int i = 0; i < N; i++) {
            next -= A[i];
            if(next == prev) {
                return i + 1;
            }
            prev += A[i];
        }
        return -1;
    }
};

```
