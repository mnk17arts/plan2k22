---
layout: post
title: Maximum Triplet product
summary:
tags:
  - geeksforgeeks
  - array
  - math
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/d54c71dc974b7db3a200eb63f34e3d1cba955d86/1)

Given an array arr of size n, the task is to find the maximum triplet product in the array.

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function maxTripletProduct() which takes an integer n and an array arr and returns the maximum triplet product in the array.

**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(1)` 

### Examples

**Example 1:**

```
Input:
n = 4
arr[] = {1, 2, 3, 5}
Output:
30
Explanation:
5*3*2 gives 30. This is the maximum possible
triplet product in the array.
```

**Example 2:**

```
Input:
n = 7
arr[] = {-3, -5, 1, 0, 8, 3, -2} 
Output:
120
Explanation: 
-3*-5*8 gives 120. This is the maximum possible triplet product in the array.
```

### Constraints

- `3 <= N <= 10^5`
- `-10^5 <= arr[i] <= 10^5`

## Solutions

```cpp

class Solution {
  public:
    long long maxTripletProduct(long long arr[], int n)
    {
    	// Complete the function
    	long long mn1 = INT_MAX, mn2 = INT_MAX, mx1 = INT_MIN, mx2 = INT_MIN, mx3 = INT_MIN;
    	for(int i = 0; i < n; i++) {
    	    if(arr[i] < mn1) {
    	        mn2 = mn1;
    	        mn1 = arr[i];
    	    }
    	    else if(arr[i] < mn2) {
    	        mn2 = arr[i];
    	    }
    	    if(arr[i] > mx1) {
    	        mx3 = mx2;
    	        mx2 = mx1;
    	        mx1 = arr[i];
    	    }
    	    else if(arr[i] > mx2) {
    	        mx3 = mx2;
    	        mx2 = arr[i];
    	    }
    	    else if(arr[i] > mx3) {
    	        mx3 = arr[i];
    	    }
    	} 
    	return max((mn1 * mn2 * mx1), (mx1 * mx2 * mx3));
    }
};

```
