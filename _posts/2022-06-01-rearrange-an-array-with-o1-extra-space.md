---
layout: post
title: Rearrange an array with O(1) extra space 
summary:
tags:
    - array
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/rearrange-an-array-with-o1-extra-space3142/1/?track=DSASP-Arrays&batchId=154#)  

Given an array `arr[]` of size N where every element is in the range from `0` to `n-1`. Rearrange the given array so that `arr[i] `becomes `arr[arr[i]]`.


**Your Task:** 
You don't need to read input or print anything. The task is to complete the function `arrange()` which takes `arr` and `N` as input parameters and rearranges the elements in the array in-place. 

**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
N = 2
arr[] = {1,0}
Output: 0 1
Explanation: 
arr[arr[0]] = arr[1] = 0.
arr[arr[1]] = arr[0] = 1.
```

**Example 2:**   
```
Input:
N = 5
arr[] = {4,0,2,1,3}
Output: 3 4 2 0 1
Explanation: 
arr[arr[0]] = arr[4] = 3.
arr[arr[1]] = arr[0] = 4.
and so on.
```

### Constraints

+ `1 <= N <= 10^7`
+ `0 ≤ arr[i] <= N`

## Solutions

```cpp
class Solution{
    public:
    // arr: input array
    // n: size of array
    //Function to rearrange an array so that arr[i] becomes arr[arr[i]]
    //with O(1) extra space.
    void arrange(long long arr[], int n) {
        // Your code here
        for(int i=0; i<n; i++)
            arr[i] += arr[arr[i]]%n*n ;
        for(int i=0; i<n; i++)
            arr[i] /= n;
    }
};
```

