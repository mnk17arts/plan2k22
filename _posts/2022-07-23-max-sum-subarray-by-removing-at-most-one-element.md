---
layout: post
title:  Max sum subarray by removing at most one element                        
summary:
tags:
    - dynamic-programming
    - array
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/max-sum-subarray-by-removing-at-most-one-element/0/?track=DSASP-DP&batchId=154)  

You are given array `A` of size `n`. You need to find the maximum-sum sub-array with the condition that you are allowed to skip at most one element. 

**Your Task:** 

Your task is to complete the function `maxSumSubarray` that take array and size as parameters and returns the maximum sum.


**Expected Time Complexity:** `O(N)`              
**Expected Auxiliary Space:** `O(N)`


### Examples

**Example 1:**   
```
Input:
n = 5
A[] = {1,2,3,-4,5}
Output: 11
Explanation: We can get maximum sum
subarray by skipping -4.
```

**Example 2:**   
```
Input:
n = 8
A[] = {-2,-3,4,-1,-2,1,5,-3}
Output: 9
Explanation: We can get maximum sum
subarray by skipping -2 as [4,-1,1,5]
sums to 9, which is the maximum
achievable sum.
```

### Constraints

+ `1 <= n <= 100`
+ `-1000 <= A[i] <= 1000`


## Solutions

```cpp
class Solution
{
    public:
    //Function to return maximum sum subarray by removing at most one element.
    int maxSumSubarray(int A[], int n) {
        //Your code here
        int l[n],r[n];
        l[0]=A[0];
        r[n-1]=A[n-1];
        int res = l[0];
        for(int i=1;i<n;i++){
            l[i] = max(A[i], l[i-1]+A[i]);
            res = max(res,l[i]);
            r[n-1-i] = max(A[n-1-i], r[n-i]+A[n-1-i]);
        }
        res = max(res,r[0]);
        for(int i=1;i<n-1;i++)
            res = max(res,l[i-1]+r[i+1]);
        return res;
    }
};
```

