---
layout: post
title: Minimum Difference in an Array 
summary:
tags:
    - sorting
    - array
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/minimum-difference-in-an-array/0/)  

Given a array of size `n`, find the minimum difference between any pair of elements in given array.

**Your Task:** 
You don't need to read or print anything. Your task is to complete the function `MinimumDifference()` which takes the array and its size as input parameters and returns the minimum difference  between any pair in given array.

**Expected Time Complexity:** `O(NlogN)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input: 
Arr = [2, 4, 5, 9, 7]
Output: 
1
Explanation: Difference between 5 and 4 is 1.
```

**Example 2:**   
```
Input: 
Arr = [3, 10, 8, 6]
Output: 
2
Explanation: Difference between 8 and 6 is 2.
```

### Constraints

+ `1 <= N <= 10^5`
+ `1 <= A[i] <= 10^9`

## Solutions

```cpp
class Solution{
    public:
    //Function to find minimum difference between any pair of elements in an array.
    int MinimumDifference(int arr[], int n)
    {
        //code here
        sort(arr, arr+n);
        int res = INT_MAX;
        for(int i=1; i<n; i++)
            res = min(res, abs(arr[i]-arr[i-1]));
        return res;
    }

};
```

