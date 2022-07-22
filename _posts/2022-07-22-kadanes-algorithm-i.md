---
layout: post
title: Kadane's Algorithm - I                       
summary:
tags:
    - dynamic-programming
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/kadanes-algorithm-i/0/?track=DSASP-DP&batchId=154#)  

Kadane's algorithm comes into picture when we want to find the maximum possible sum in an array when summing the contiguous elements of the array.

You are given an array. Find the maximum possible sum of contiguous elements of the array ending at each position in the array. Also, return the overall maximum that we can achieve.

**Your Task:** 

This is a function problem. You don't need to take any input. Just complete the function `maximumSum()` that takes the integer array and its size as inputs and prints the maximum contiguous subarray sum ending at each position in the array. Also, return the overall maximum.


**Expected Time Complexity:** `O(N)`              
**Expected Auxiliary Space:** `O(N)`


### Examples

**Example 1:**   
```
Input:
N = 6
arr[] = {5,-2,-3,32,-5,65}
Output: 5 3 0 32 27 92
        92
Explanation: Maximum sum at each index is
5, 3, 0, 32, 27, 92. And, maximum sum for
contiguous array is 92.
```

**Example 2:**   
```
Input:
N = 5
arr[] = {-9,-8,8,3,-4}
Output: -9 -8 8 11 7
         11
```

### Constraints

+ `1 <= n <= 10^6`
+ `-10^3 <= arr[i] <= 10^3`


## Solutions

```cpp
class Solution
{
    public:
    //Function to print the maximum contiguous subarray sum ending at each 
    //position in the array and return the overall maximum.
    long long maximumSum(int arr[], int sizeOfArray)
    {
       //code here
       long long res = INT_MIN, pre = INT_MIN;
       for(int i=0;i<sizeOfArray;i++){
           pre = max((long long)arr[i],pre+arr[i]);
           cout << pre << " "; 
           res = max(res,pre);
       }
       cout<<endl;
       return res;
    }
};
```

