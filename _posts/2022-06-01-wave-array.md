---
layout: post
title: Wave Array
summary:
tags:
    - array
    - sorting
    - geeksforgeeks
    - cpp
    - easy
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/wave-array-1587115621/1/?track=DSASP-Arrays&batchId=154#)  

Given a sorted array `arr[]` of distinct integers. Sort the array into a wave-like array and return it
In other words, arrange the elements into a sequence such that `arr[1] >= arr[2] <= arr[3] >= arr[4] <= arr[5].....`

If there are multiple solutions, find the lexicographically smallest one.


**Your Task:** 
The task is to complete the function `convertToWave()`, which converts the given array to a wave array.
**NOTE:** The given array is sorted in ascending order.

**Expected Time Complexity**: `O(n)`.     
**Expected Auxiliary Space**: `O(1)`. 


### Examples

**Example 1:**   
```
Input:
n = 5
arr[] = {1,2,3,4,5}
Output: 2 1 4 3 5
Explanation: Array elements after 
sorting it in wave form are 
2 1 4 3 5.
```

**Example 2:**   
```
Input:
n = 6
arr[] = {2,4,7,8,9,10}
Output: 4 2 8 7 10 9
Explanation: Array elements after 
sorting it in wave form are 
4 2 8 7 10 9.
```

### Constraints

+ `1 <= n <= 10^6`
+ `0 ≤ arr[i] <= 10^7`

## Solutions

```cpp
class Solution{
    public:
    // arr: input array
    // n: size of array
    //Function to sort the array into a wave-like array.
    void convertToWave(int n, vector<int>& arr){
        
        // Your code here
        for(int i=0; (i+1)<n; i+=2){
            swap(arr[i],arr[i+1]);
        }
        
    }
};
```

