---
layout: post
title: Closet 0s 1s and 2s 
summary:
tags:
    - sorting
    - array
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/sort-an-array-of-0s-1s-and-2s-1587115621/0/)  

Given an array of `0`s, `1`s, and `2`s. Arrange the array elements such that all `0`s come first, followed by all the `1`s and then, all the `2`s.

**Note**: Do not use the inbuilt sort function.

**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `segragate012()` which takes the array `arr[]` and the size of the array as inputs and updates the array `arr[]` such that all the `0`s come before the `1`s and all the `1`s come before the `2`s.

**Expected Time Complexity:** `O(n)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input: N = 5, arr[] = {0, 2, 1, 2, 0}
Output: 0 0 1 2 2
```

**Example 2:**   
```
Input: N = 3, arr[] = {0, 1, 0}
Output: 0 0 1
```

### Constraints

+ `1 <= N <= 10^6`
+ `0 <= arr[i] <= 2`

## Solutions

```cpp
class Solution{
    public:
    // The function should do the stated modifications in the given array arr[]
    // Do not return anything.
    
    // arr[]: Input Array
    // N: Size of the Array arr[]
    //Function to segregate 0s, 1s and 2s in sorted increasing order.
    void segragate012(int arr[], int N){
        // Your Code Here
        int low = 0, mid = 0, high = N-1;
        while( mid <= high){
            if(arr[mid] == 0) swap(arr[low++],arr[mid++]);
            else if(arr[mid] == 1) mid++;
            else swap(arr[mid],arr[high--]);
        }
    }
};
```

