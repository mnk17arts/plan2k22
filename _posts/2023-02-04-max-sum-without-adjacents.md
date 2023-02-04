---
layout: post
title: Max Sum without Adjacents                     
summary:
tags:
    - geeksforgeeks
    - array
    - dynamic-programming
    - cpp
    - easy
minute: 10+ min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/7a33c749a79327b2889d420dd80342fff33aac6d/1)

Given an array Arr of size N containing positive integers. Find the maximum sum of a subsequence such that no two numbers in the sequence should be adjacent in the array. 

**Your Task:** 

You don't need to read input or print anything. Your task is to complete the function findMaxSum() which takes the array of integers arr and n as parameters and returns an integer denoting the answer. It is guaranteed that your answer will always fit in the 32-bit integer



**Expected Time Complexity:** `O(N)`              
**Expected Auxiliary Space:** `O(1)` 



### Examples

**Example 1:**   
```
Input:
N = 6
Arr[] = {5, 5, 10, 100, 10, 5}
Output: 110
Explanation: If you take indices 0, 3
and 5, then Arr[0]+Arr[3]+Arr[5] =
5+100+5 = 110.
```

**Example 2:**   
```
Input:
N = 4
Arr[] = {3, 2, 7, 10}
Output: 13
Explanation: 3 and 10 forms a non
continuous  subsequence with maximum
sum.
```

### Constraints

+ `1 ≤ N ≤ 10^6`
+ `1 ≤ Arri ≤ 10^7`

## Solutions

```cpp

class Solution{
public:	
	// calculate the maximum sum with out adjacent
	int findMaxSum(int *arr, int n) {
	    // code here
	    if(n==1) return arr[0];
	    int mArr[n];
	    mArr[0] = arr[0];
	    mArr[1] = max(arr[1], mArr[0]);
	    for(int i=2; i<n; i++) {
	        arr[i] += mArr[i-2];
	        mArr[i] = max(arr[i], mArr[i-1]);
	    }
	    return max(mArr[n-1], mArr[n-2]);
	}
};

```
