---
layout: post
title: Binary Array Sorting 
summary:
tags:
    - sorting
    - 2pointers
    - array
    - geeksforgeeks
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/binary-array-sorting-1587115620/0/#)  

Given a binary array `A[]` of size `N`. The task is to arrange the array in increasing order.
Note: The binary array contains only `0`  and `1`.

**Your Task:** 
Your Task: This is a function problem. You only need to complete the function `binSort()` that takes the array `A[]` and it's size `N` as parameters and sorts the array. The printing is done automatically by the driver code. 


**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input: 
5
1 0 1 1 0

Output: 
0 0 1 1 1

Explanation: 
After arranging the elements in 
increasing order, elements will be as 
0 0 1 1 1.
```

**Example 2:**   
```
Input:
10
1 0 1 1 1 1 1 0 0 0

Output: 
0 0 0 0 1 1 1 1 1 1

Explanation: 
After arranging the elements in 
increasing order, elements will be 
0 0 0 0 1 1 1 1 1 1.
```

### Constraints

+ `1 <= N <= 10^6`
+ `0 <= arr[i] = 1` 

## Solutions

```cpp
class Solution{
    public:
    // A[]: input array
    // N: input array
    //Function to sort the binary array.
    void binSort(int arr[], int N)
    {
       //Your code here
       
       /**************
        * No need to print the array
        * ************/
        int i = -1, j = N;
        while(i <= j) {
            while(arr[++i] == 0);
            while(arr[--j] > 0);
            if(i > j) return;
            swap(arr[i], arr[j]);
        }
    }
};
```

