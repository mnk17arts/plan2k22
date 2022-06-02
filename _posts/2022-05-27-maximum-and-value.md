---
layout: post
title:  Maximum AND Value
summary:
tags:
    - bit-manipulation
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/maximum-and-value-1587115620/1)  

Given an array `arr[]` of `N` positive elements. The task is to find the Maximum **AND** Value generated by any pair`(arri, arrj)` from the array such that `i != j`.
Note: **AND** is bitwise '`&`' operator.

**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `maxAND()` which takes the array elements and `N` (size of the array) as input parameters and returns the maximum AND value generated by any pair in the array. 

**Expected Time Complexity**: `O(N * log M)`, where `M` is the maximum element of the array.     
**Expected Auxiliary Space**: `O(1)`.


### Examples

**Example 1:**   
```
Input: 
N = 4
arr[] = {4, 8, 12, 16}
Output: 8
Explanation:
Pair (8,12) has the Maximum AND Value 8.
```

**Example 2:**   
```
Input:
N = 4
arr[] = {4, 8, 16, 2}
Output: 0
Explanation: Any two pairs of the array has 
Maximum AND Value 0.
```

### Constraints

+ `1 <= N <= 10^5`
+ `1 <= arr[i] <= 10^5`

## Solutions

```cpp
class Solution
{
    public:
    // Function for finding maximum AND value.
    int maxAND (int arr[], int n)
    {
        // Your code here
        int res = 0;
        for (int i = 31; i >= 0; i--) {
            int max = 0, tres = res | (1 << i);
            for (int j = 0; j < n; j++) {
                if ( (tres & arr[j]) == tres)  {
                    max++;
                }
            }
            if(max >= 2)
                res |= (1 << i);
        }
        return res;
    }
};
```
