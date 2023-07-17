---
layout: post
title: Count Pairs With Given Sum
summary:
tags:
  - geeksforgeeks
  - array
  - hash
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/count-pairs-with-given-sum5022/1s)

Given an array of N integers, and an integer K, find the number of pairs of elements in the array whose sum is equal to K.

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function getPairsCount() which takes arr[], n and k as input parameters and returns the number of pairs that have sum KS and integer X as input parameters and returns true if students in all rooms can use wifi or false otherwise.

**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**

```
Input:
N = 4, K = 6
arr[] = {1, 5, 7, 1}
Output: 2
Explanation: 
arr[0] + arr[1] = 1 + 5 = 6 
and arr[1] + arr[3] = 5 + 1 = 6.
```

**Example 2:**

```
Input:
N = 4, K = 2
arr[] = {1, 1, 1, 1}
Output: 6
Explanation: 
Each 1 will produce sum 2 with any 1.
```

### Constraints

- `1 ≤ N ≤ 10^5`
- `1 ≤ K ≤ 10^7`
- `1 ≤ A[i] ≤ 10^6`

## Solutions

```cpp

class Solution {
  public:
    int getPairsCount(int arr[], int n, int k) {
        int cnt = 0;
        unordered_map<int,int> mp;
        for(int i = 0; i < n; i++) {
            if(mp[arr[i]] != 0) 
                cnt += mp[arr[i]];
            mp[k-arr[i]]++;
        }
        return cnt;
    }
};

```
