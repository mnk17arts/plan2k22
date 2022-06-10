---
layout: post
title: Closer to sort 
summary:
tags:
    - sorting
    - searching
    - binary-search
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/closer-to-sort-1587115620/0/#)  

Given an array `arr[]`(`0`-based indexing) of `N` integers which is closer sorted (defined below) and an element `x`. The task is to find the index of element `x` if it is present. If not present, then print `-1`.
**Closer Sorted**: The first array is sorted, but after sorting some elements are moved to either of the adjacent positions, i.e, maybe to the `arr[i+1]` or `arr[i-1]`.

**Note:** You may assume that the array does not contain any duplicate elements.

**Your Task:** 
This is a function problem. You only need to complete the function `closer()` that `arr`, `N`, and `x` as parameters and returns the index. If the element is not present, return `-1`.

**Expected Time Complexity:** `O(Log(N))`  
**Expected Auxiliary Space:** `O(1)` 

### Examples

**Example 1:**   
```
Input: N = 5, A[] = [3 2 10 4 40], x = 2
Output: 1
Explanation: 2 is present at index 1 
(0-based indexing) in the given array.
```

**Example 2:**   
```
Input: N = 4, A[] = [2 1 4 3], x = 5
Output: -1
Explanation: 
5 is not in the array so the output will 
be -1.
```

### Constraints

+ `1 <= N<= 10^6`
+ `1 <= arr[i],x <= 10^9`

## Solutions

```cpp
class Solution{
    public:
    // arr[]: input array
    // n: size of array
    // x: element to find index
    //Function to find index of element x in the array if it is present.
    int closer(int arr[],int n, int x)
    {
        //Your code here
        int l = 0, r = n-1;
        while(l <= r){
            int m = l + (r-l)/2 ;
            if(arr[m] == x) return m;
            else if(m != r && arr[m] > x && arr[m+1] > x) r = m-1;
            else l = m+1;
        }
        return -1;
    }

};
```

