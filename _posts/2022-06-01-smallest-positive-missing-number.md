---
layout: post
title: Smallest Positive missing number   
summary:
tags:
    - array
    - searching
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/smallest-positive-missing-number-1587115621/1#)  

You are given an array `arr[]` of `N` integers including `0`. The task is to find the smallest positive number missing from the array. 


**Your Task:** 
The task is to complete the function `missingNumber()` which returns the smallest positive missing number in the array.

**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
N = 5
arr[] = {1,2,3,4,5}
Output: 6
Explanation: Smallest positive missing 
number is 6.
```

**Example 2:**   
```
Input:
N = 5
arr[] = {0,-10,1,3,-20}
Output: 2
Explanation: Smallest positive missing 
number is 2.
```

### Constraints

+ `1 <= N <= 10^6`
+ `-10^6 ≤ arr[i] <= 10^6`

## Solutions

```cpp
class Solution{
    public:
    //Function to find the smallest positive number missing from the array.
    int missingNumber(int arr[], int n) 
    { 
        // Your code here
        int one = 0;
        for(int i=0; i<n; i++){
            if(arr[i] == 1) one=1;
            if(arr[i] <=0 || arr[i]>n)
                arr[i]=0;
            else
                arr[i] -= 1;
        }
        if(!one) return 1;
        for(int i=0; i<n; i++)
            arr[arr[i]%n]+=n;
        for(int i=0; i<n; i++){
            arr[i] /= n;
            if(arr[i] == 0)
                return i+1;
        }
        return n+1;
    } 
};
```

