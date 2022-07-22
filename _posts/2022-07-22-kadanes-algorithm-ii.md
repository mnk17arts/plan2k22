---
layout: post
title: Kadane's Algorithm - II                       
summary:
tags:
    - dynamic-programming
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/kadanes-algorithm-ii/0/?track=DSASP-DP&batchId=154#)  

You are given an array `arr` of size `sizeOfArr`. You need to find the maximum sum in the array provided that you cannot sum neighboring elements or adjacent elements.

**Your Task:** 

This is a function problem. You only need to complete the function `maximumSum()` that takes array and `sizeOfArray` and returns the maximum sum of the array provided that you cannot sum neighboring elements.


**Expected Time Complexity:** `O(N)`              
**Expected Auxiliary Space:** `O(N)`


### Examples

**Example 1:**   
```
Input:
sizeOfArr = 4
arr[] = {4,5,6,7,8}
Output: 18
Explanation:The given elements are 4 5 6 7 8
For 4, the maximum sum will be 4 as no
element other than 4 from index 0 to 0
For 5, the maximum sum will be 5 as we cannot
add 4 and 5(neighboring elements).
For 6, the maximum sum will be 10 as we can
add 6 and 4.
For 7, the maximum sum will be 12 as we can
add 7 and 5.
For 8, the maximum sum will be 18 as we can
add 4 and 6 and 8.
```

**Example 2:**   
```
Input:
sizeOfArr = 5
arr[] = {-9,-8,8,3,-4}
Output: 8
```

### Constraints

+ `1 <= n <= 10^4`
+ `-10^3 <= arr[i] <= 10^3`


## Solutions

```cpp
class Solution
{
    public:
    //Function to return the maximum sum without adding adjacent elements.
    long long maximumSum(int arr[], int sizeOfArray)
    {
      //Your code here
      if(sizeOfArray==1) return arr[0];
      if(sizeOfArray==2) return max(arr[0],arr[1]);
      long long prepre = arr[0], pre = max(arr[0],arr[1]);
      for(int i=2;i<sizeOfArray;i++){
          long long temp = max((long long)arr[i],max(arr[i]+prepre,pre));
          prepre = pre ;
          pre = temp;
      }
      return pre;
    }
};
```

