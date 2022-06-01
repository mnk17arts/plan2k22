---
layout: post
title: Rotate Array
summary:
tags:
    - array
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/rotate-array-by-n-elements-1587115621/1/)  

Given an unsorted array `arr[]` of size `N`. Rotate the array to the left (counter-clockwise direction) by `D` steps, where `D` is a positive integer. 


**Your Task:** 
Complete the function `rotateArr()` which takes the array, `D` and `N` as input parameters and rotates the array by `D` elements. The array must be modified in-place without using extra space.

**Expected Time Complexity**: `O(N)`.     
**Expected Auxiliary Space**: `O(1)`.


### Examples

**Example 1:**   
```
Input:
N = 5, D = 2
arr[] = {1,2,3,4,5}
Output: 3 4 5 1 2
Explanation: 1 2 3 4 5  when rotated
by 2 elements, it becomes 3 4 5 1 2.
```

**Example 2:**   
```
Input:
N = 10, D = 3
arr[] = {2,4,6,8,10,12,14,16,18,20}
Output: 8 10 12 14 16 18 20 2 4 6
Explanation: 2 4 6 8 10 12 14 16 18 20 
when rotated by 3 elements, it becomes 
8 10 12 14 16 18 20 2 4 6.
```

### Constraints

+ `1 <= N,D <= 10^6`
+ `0 <= A[i] <= 10^5`

## Solutions

```cpp
class Solution{
public:
    //Function to rotate an array by d elements in counter-clockwise direction. 
    void rotateArr(int a[], int d, int n){
        // code here
        d = d%n;
        int temp[d];
        for(int i=0;i<d;i++)
            temp[i] = a[i];
        for(int i=d;i<n;i++)
            a[i-d] = a[i];
        for(int i=0;i<d;i++)
            a[n-d+i] = temp[i];
    }
};
```

