---
layout: post
title: Minimum Number in a sorted rotated array 
summary:
tags:
    - array
    - binary-search
    - searching
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/minimum-number-in-a-sorted-rotated-array-1587115620/1#)  

Given an array of distinct elements which was initially sorted. This array is rotated at some unknown point. The task is to find the minimum element in the given sorted and rotated array.

**Your Task:** 
The task is to complete the function `minNumber()` which takes the array `arr[]` and its starting and ending indices (`low` and `high`) as inputs and returns the minimum element in the given sorted and rotated array.

**Expected Time Complexity:** `O(logN)`  
**Expected Auxiliary Space:** `O(LogN)`

### Examples

**Example 1:**   
```
Input:
N = 10
arr[] = {2,3,4,5,6,7,8,9,10,1}
Output: 1
Explanation: The array is rotated 
once anti-clockwise. So minium 
element is at last index (n-1) 
which is 1.
```

**Example 2:**   
```
Input:
N = 5
arr[] = {3,4,5,1,2}
Output: 1
Explanation: The array is rotated 
and the minimum element present is
at index (n-2) which is 1.
```

### Constraints

+ `1 <= N <= 10^7`
+ `1 <= arr[i] = 10^7`

## Solutions

```cpp
class Solution{
    public:
    //Function to find the minimum element in sorted and rotated array.
    int minNumber(int arr[], int low, int high)
    {
        // Your code here
        while(low <= high){
            int mid = low + (high - low) / 2;
            if(arr[mid] > arr[high]) low = mid + 1; 
            else if(arr[mid] < arr[low]) high = mid;
            else return arr[low];
        }
        return -1;
    }
};
```

