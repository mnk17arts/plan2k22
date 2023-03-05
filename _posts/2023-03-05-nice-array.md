---
layout: post
title: Nice Array
summary:
tags:
  - geeksforgeeks
  - array
  - 2pointers
  - cpp
  - easy
minute: 10+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/contest/gfg-weekly-coding-contest-92/problems#)

You are given an array arr of n integers. An array is nice if for each index i, the value of arr[i] = i. Your task is to find the length of the longest subarray of the array arr which is nice. Consider 1-based indexing.

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function niceSubarray() which takes an integer n, and an array arr[] as input parameters and returns the length of the longest nice subarray.

**Expected Time Complexity:** `O(n)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**

```
Input:
n = 7
arr = {2,1,2,3,1,2,2}
Output:
3
Explanation:
The subarray {1,2,3} is the longest nice subarray.
```

**Example 2:**

```
Input:
n = 4
arr = {3,5,2,6}
Output:
0
Explanation:
There is no nice subarray.
```

### Constraints

- `1 ≤ N  <= 10^5`
- `1 ≤ arr[i] ≤ 10^5`

## Solutions

```cpp

class Solution{
  public:
    int niceSubarray(int n, vector<int> &arr) {
        // code here
        int res = 0, cur = 0;
        for(int i = 0; i < n; i++) {
            cur = i;
            while(cur < n && arr[cur] == cur - i + 1) {
                cur++;
            
            }
            res = max(res, cur - i);
        }
        return res;
    }
};

```
