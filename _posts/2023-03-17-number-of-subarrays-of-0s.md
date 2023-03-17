---
layout: post
title: Number of Subarrays of 0's
summary:
tags:
  - geeksforgeeks
  - array
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/0960a833f70b09c59444ea487f99729929fc8910/1)

You are given an array arr  of length N of 0's and 1's. Find the total number of subarrays of 0's

**Your Task:**

Your task is to complete the function no_of_subarrays(), which takes an integer N and an integer array arr as the input parameters and returns an integer denoting the total number of subarrays of 0's.

**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(1)` 

### Examples

**Example 1:**

```
Input:
N = 4
arr[] = {0, 0, 1, 0}
Output:
4
Explanation:
Following are the subarrays of
length 1: {0}, {0}, {0} - 3
length 2: {0, 0} - 1
Total Subarrays: 3 + 1 = 4
```

**Example 2:**

```
Input:
N = 4
arr[] = {0, 0, 0, 0}
Output:
10
Explanation:
Following are the subarrays of
length 1: {0}, {0}, {0}, {0} - 4
length 2: {0, 0}, {0, 0}, {0, 0} - 3
length 3: {0, 0, 0}, {0, 0, 0} - 2
length 4: {0, 0, 0, 0} - 1
Total Subarrays: 4 + 3 + 2 + 1 = 10
```

### Constraints

- `1 <= N <= 10^6`
- `0 <= arr[i] <= 1`

## Solutions

```cpp

class Solution {
  public:
    long long int no_of_subarrays(int n, vector<int> &arr) {
    // Write your code here.
    	long count = 0;
		long ans = 0;
		for(int i = 0; i < n; i++){
		    if(arr[i] == 0){
		        count++;
		        if(i == n - 1){
		            ans += (count * (count + 1)) / 2;
		        }
		    }else{
		        ans += (count * (count + 1)) / 2;
		        count = 0;
		    }		  
		}
		return ans;
    }
};

```
