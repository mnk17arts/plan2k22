---
layout: post
title: Left Index 
summary:
tags:
    - searching
    - array
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/left-index-1587115620/1/)  

Given a sorted array of positive integers (elements may be repeated) and a number x. The task is to find the leftmost index of x in the given array.

**Your Task:** 
The task is to complete the function `leftIndex()` which takes the array `arr[]`, its size `N` and an integer `x` as inputs and returns the index of leftmost occurrence of `x` in given input array. It returns `-1` if element is not present in the array.

**Expected Time Complexity:** `O(LogN)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
N = 10
arr[] = {1,1,2,2,3,4,5,5,6,7}
x = 1
Output: 0
Explanation: 1 is present two times
in the array and its leftmost index 
is 0.
```

**Example 2:**   
```
Input:
N = 7
arr[] = {10,20,20,20,20,20,20}
x = 20
Output: 1
Explanation: 20 is present 5 time, 
but its leftmost index is 1.
```

### Constraints

+ `1 <= N <= 10^6`
+ `0 <= arr[i] <= 10^6`
+ `1 <= x <= 10^6`

## Solutions

```cpp
class Solution{
    public:
    int leftIndex(int N, int arr[], int X){
        int left = 0, right = N-1;
        while(left <= right){
            int mid = left + (right-left)/2;
            if(arr[mid] == X){
                if(mid == 0 || arr[mid-1] != X) return mid;
                else right = mid - 1;
            }
            else if(arr[mid] < X)
                left = mid+1;
            else
                right = mid-1;
        }
        return -1;    
    }
};
```

