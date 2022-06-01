---
layout: post
title: Minimum adjacent difference in a circular array 
summary:
tags:
    - array
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/minimum-absloute-difference-between-adjacent-elements-in-a-circular-array-1587115620/1)  

Given an array `Arr` of `n` integers arranged in a circular fashion. Your task is to find the minimum absolute difference between adjacent elements.


**Your Task:** 
The task is to complete the function `minAdjDiff()` which returns the minimum difference between adjacent elements in circular array.

**Expected Time Complexity**: `O(N)`.     
**Expected Auxiliary Space**: `O(1)`.


### Examples

**Example 1:**   
```
Input:
n = 7
Arr[] = {8,-8,9,-9,10,-11,12}
Output: 4
Explanation: The absolute difference 
between adjacent elements in the given 
array are as such: 16 17 18  19 21 23 4
(first and last). Among the calculated 
absolute difference the minimum is 4.
```

**Example 2:**   
```
Input:
n = 8
Arr[] = {10,-3,-4,7,6,5,-4,-1}
Output: 1
Explanation: The absolute difference 
between adjacent elements in the given 
array are as such: 13 1 11 1 1 9 3 11
(first and last).  Among the calculated 
absolute difference, the minimum is 1.
```

### Constraints

+ `2 <= N <= 10^6`
+ `-10^6 <= arr[i] <= 10^6`

## Solutions

```cpp
class Solution{
    public:
    //Function to find minimum adjacent difference in a circular array.
    // arr[]: input array
    // n: size of array
    int minAdjDiff(int arr[], int n){    
        // Your code here
        int res = abs(arr[0]-arr[n-1]);
        for(int i=0;i<n-1; i++)
            res = min(res, abs(arr[i]-arr[i+1]));
        return res;
    }
};
```

