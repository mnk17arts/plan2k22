---
layout: post
title: Count the triplets
summary:
tags:
  - geeksforgeeks
  - 2pointers
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/count-the-triplets4615/1)

Given an array of distinct integers. The task is to count all the triplets such that sum of two elements equals the third element.

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function countTriplet() which takes the array arr[] and N as inputs and returns the triplet count


**Expected Time Complexity:** `O(N^2)`  
**Expected Auxiliary Space:** `O(1)` 

### Examples

**Example 1:**

```
Input: 
N = 4 
arr[] = {1, 5, 3, 2}
Output: 2 
Explanation: There are 2 triplets:
 1 + 2 = 3 and 3 +2 = 5
```

**Example 2:**

```
Input: 
N = 3
arr[] = {2, 3, 4}
Output: 0
Explanation: No such triplet exits
```

### Constraints

- `1 ≤ N ≤ 1000`
- `1 ≤ arr[i] ≤ 10^5`

## Solutions

```cpp

class Solution{
  public:
	int countTriplet(int arr[], int n)
	{
	    // Your code goes here
	    int res = 0;
	    if(n < 3) {
	        return res;
	    }
	    unordered_set<int> set(arr, arr+n);

	    for(int i = 0; i < n; i++) {
	        for(int j = i + 1; j < n; j++) {
	            if(set.find(arr[i] + arr[j]) != set.end()) {
	                res++;
	            }
	        }
	    }
	    return res;
	}
};

```
