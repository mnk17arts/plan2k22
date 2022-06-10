---
layout: post
title: Kth smallest element
summary:
tags:
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/kth-smallest-element5545-1587115620/0/#)  

Given an array `arr[]` of `N` positive integers and a number `K`. The task is to find the `k`th smallest element in the array.

**Your Task:** 
You  don't need to read inputs or print anything. Complete the method `kthSmallest()` which takes array `arr[]`, size of the array `n` and value `k` as input parameters and returns `k`th smallest element.

**Expected Time Complexity:** `O(NlogK)`  
**Expected Auxiliary Space:** `O(K)`

### Examples

**Example 1:**   
```
Input: 
N = 5, K = 3
arr[] = {3,5,4,2,9}

Output: 
4

Explanation: 
Third smallest element in the array is 4.
```

**Example 2:**   
```
Input:
N = 5, k = 5
arr[] = {4,3,7,6,5}

Output: 
7

Explanation: 
Fifth smallest element in the array is 7.
```

### Constraints

+ `1 <= N <= 10^6`
+ `1 <= A[i] <= 10^6`
+ `1 <= K <= N`
Array do not contains duplicates.   

## Solutions

```cpp
class Solution{
    public:
    int lomutoPartition(int arr[], int l, int r){
        int pivot = arr[r];
        int j = l;
        for(int i=l; i<r; i++)
            if(arr[i] < pivot)
                swap(arr[j++],arr[i]);
        swap(arr[r],arr[j]);
        return j;
    }
    //Function to find the kth smallest element in the array.
    int kthSmallest(int arr[], int n, int k)
    {
        // Your code here
        int l = 0, r = n-1;
        while(l<=r){
            int p = lomutoPartition(arr, l , r);
            if(p == k-1) return arr[p];
            else if(p > k-1) r = p-1;
            else l = p + 1;
        }
        return -1;
    }

};
```

