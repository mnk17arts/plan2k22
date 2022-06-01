---
layout: post
title: Max Circular Subarray Sum
summary:
tags:
    - array
    - geeksforgeeks
    - cpp
    - hard
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/max-circular-subarray-sum-1587115620/1/)  

Given an array `arr[]` of `N` integers arranged in a circular fashion. Your task is to find the maximum contiguous subarray sum.

.

**Your Task:** 
The task is to complete the function `circularSubarraySum()` which returns a sum of the circular subarray with maximum sum.

**Expected Time Complexity**: `O(N)`.     
**Expected Auxiliary Space**: `O(1)`.


### Examples

**Example 1:**   
```
Input:
N = 7
arr[] = {8,-8,9,-9,10,-11,12}
Output:
22
Explanation:
Starting from the last element
of the array, i.e, 12, and 
moving in a circular fashion, we 
have max subarray as 12, 8, -8, 9, 
-9, 10, which gives maximum sum 
as 22.
```

**Example 2:**   
```
Input:
N = 8
arr[] = {10,-3,-4,7,6,5,-4,-1}
Output:
23
Explanation: Sum of the circular 
subarray with maximum sum is 23
```

### Constraints

+ `1 <= N <= 10^6`
+ `-10^6 <= Arr[i] <= 10^6`

## Solutions

```cpp
class Solution
{
    public:
    // arr: input array
    // num: size of array
    //Function to find maximum circular subarray sum.
    int maxSubarraySum(int arr[], int num){
        int cur = arr[0], res=arr[0];
        for(int i=1; i<num; i++){
            cur = max(arr[i], cur+arr[i]);
            res = max(res, cur);
        }
        return res;
    }    
    int circularSubarraySum(int arr[], int num){
        
        // your code here
        int linear = maxSubarraySum(arr, num);
        if(linear < 0)
            return linear;
        int cur = 0;
        for(int i=0; i<num; i++){
            cur += arr[i];
            arr[i] *= -1;
        }
        int circular = cur + maxSubarraySum(arr, num);
        return max(linear, circular);
    }
};
```

