---
layout: post
title: Binary Search
summary:
tags:
  - geeksforgeeks
  - array
  - binary-search
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/binary-search-1587115620/1)

Given a sorted array of size N and an integer K, find the position at which K is present in the array using binary search

**Your Task:**

You dont need to read input or print anything. Complete the function binarysearch() which takes arr[], N and K as input parameters and returns the index of K in the array. If K is not present in the array, return -1.



**Expected Time Complexity:** `O(LogN)`  
**Expected Auxiliary Space:** `O(LogN)`

### Examples

**Example 1:**

```
Input:
N = 5
arr[] = {1 2 3 4 5} 
K = 4
Output: 3
Explanation: 4 appears at index 3.
```

**Example 2:**

```
Input:
N = 5
arr[] = {11 22 33 44 55} 
K = 445
Output: -1
Explanation: 445 is not present.
```

### Constraints

- `1 ≤ N ≤ 10^5`
- `1 ≤ arr[i], K ≤ 10^6`

## Solutions

```cpp

class Solution{
  public:
    int binarysearch(int arr[], int n, int k) {
        // code here
        int left = 0, right = n - 1;
        while(left <= right) {
            int mid = (left + right) >> 1;
            if(arr[mid] < k) {
                left = mid + 1;
            }
            else if(arr[mid] > k) {
                right = mid - 1;
            }
            else {
                return mid;
            }
        }
        return -1;
    }
};

```
