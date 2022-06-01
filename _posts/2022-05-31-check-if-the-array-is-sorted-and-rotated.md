---
layout: post
title:  Check if array is sorted and rotated
summary:
tags:
    - array
    - sorting
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/check-if-array-is-sorted-and-rotated-clockwise-1587115620/1)  

Given an array `arr[]` of `N` distinct integers, check if this array is Sorted (non-increasing or non-decreasing) and Rotated counter-clockwise. Note that input array may be sorted in either increasing or decreasing order, then rotated.
A sorted array is not considered as sorted and rotated, i.e., there should be at least one rotation.

**Your Task:** 
The task is to complete the function `checkRotatedAndSorted()` which returns `true` if an array is sorted and rotated clockwise otherwise `false`.

**Expected Time Complexity**: `O(N)`.     
**Expected Auxiliary Space:**   `O(1)`.


### Examples

**Example 1:**   
```
Input:
N = 4
arr[] = {3,4,1,2}
Output: Yes
Explanation: The array is sorted 
(1, 2, 3, 4) and rotated twice 
(3, 4, 1, 2).
```

**Example 2:**   
```
Input:
N = 3
arr[] = {1,2,3}
Output: No
Explanation: The array is sorted 
(1, 2, 3) is not rotated.
```

### Constraints

+ `1 <= N <= 10^6`
+ `1 <= A[i] <= 10^6`

## Solutions

```cpp
class Solution
{
    public:
    // arr: input array
    // num: length of array
    // This function returns true or false
    //Function to check if array is sorted and rotated.
    bool checkIfIncreasingAndRotated(int a[], int n){
        int flip = 0;
        for(int i=1; i<n; i++){
            if(a[i] < a[i-1])
                flip++;
        }
        if(a[0] < a[n-1]) return false;
        return flip==1;
    }
    
    bool checkIfDecreasingAndRotated(int a[], int n){
        int flip = 0;
        for(int i=1; i<n; i++){
            if(a[i] > a[i-1])
                flip++;
        }
        if(a[0] > a[n-1]) return false;
        return flip==1;
    }
    
    bool checkRotatedAndSorted(int arr[], int num){
        
        int n = num;
        if(n < 3) return true;
        return checkIfIncreasingAndRotated(arr, n) || checkIfDecreasingAndRotated(arr, n);
    }
};
```

