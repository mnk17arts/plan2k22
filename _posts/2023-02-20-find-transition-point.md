---
layout: post
title: Find Transition Point
summary:
tags:
  - geeksforgeeks
  - array
  - binary-search
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/find-transition-point-1587115620/1)

Given a sorted array containing only 0s and 1s, find the transition point.

**Your Task:**

You don't need to read input or print anything. The task is to complete the function transitionPoint() that takes array and N as input parameters and returns the 0 based index of the position where "0" ends and "1" begins. If array does not have any 1s, return -1. If array does not have any 0s, return 0.


**Expected Time Complexity:** `O(LogN)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**

```
Input:
N = 5
arr[] = {0,0,0,1,1}
Output: 3
Explanation: index 3 is the transition 
point where 1 begins.
```

**Example 2:**

```
Input:
N = 4
arr[] = {0,0,0,0}
Output: -1
Explanation: Since, there is no "1",
the answer is -1.
```

### Constraints

- `1 ≤ N ≤ 500000`
- `0 ≤ arr[i] ≤ 1`

## Solutions

```cpp

int transitionPoint(int arr[], int n) {
    // code here
    int l = 0, r = n - 1, res = -1;
    while(l <= r) {
        int mid = l + (r - l) / 2;
        if(arr[mid] == 0) {
            l = mid + 1;
        }
        else {
            res = mid;
            r = mid - 1;
        }
    }
    return res;
}

```
