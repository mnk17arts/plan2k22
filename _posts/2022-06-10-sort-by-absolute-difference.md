---
layout: post
title: Sort by Absolute Difference 
summary:
tags:
    - sorting
    - array
    - merge-sort
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/sort-by-absolute-difference-1587115621/0/#)  

Given an array of `N` elements and a number `K`. The task is to arrange array elements according to the absolute difference with `K`, i. e., element having minimum difference comes first and so on.
**Note** : If two or more elements are at equal distance arrange them in same sequence as in the given array.


**Your Task:** 
This is a functional problem. You only need to complete the function `sortABS()`.

**Expected Time Complexity:** `O(NlogN)`  
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input: N = 5, K = 7
arr[] = {10, 5, 3, 9, 2}
Output: 5 9 10 3 2
Explanation: Sorting the numbers accoding to 
the absolute difference with 7, we have 
array elements as 5, 9, 10, 3, 2.
```

**Example 2:**   
```
Input: N = 5, K = 6
arr[] = {1, 2, 3, 4, 5}
Output: 5 4 3 2 1
Explanation: Sorting the numbers according to 
the absolute difference with 6, we have array 
elements as 5 4 3 2 1.
```

### Constraints

+ `1 <= N <= 10^5`
+ `1 <= K <= 10^5`

## Solutions

```cpp
class Solution{
    public:
    void merge(int a[], int l, int m, int r, int k){
        int t[r-l+1];
        int i=l, j=m+1, x=0;
        while( i <= m && j<=r){
            if(abs(a[i]-k) < abs(a[j]-k)) t[x++] = a[i++];
            else if(abs(a[i]-k) > abs(a[j]-k)) t[x++] = a[j++];
            else {
                if(i<j) t[x++] = a[i++];
                else t[x++] = a[j++];
            }
        }
        while( i <= m) t[x++] = a[i++];
        while( j <= r) t[x++] = a[j++];
        
        for(int j=l ; j<=r; j++)
            a[j] = t[j-l];
    }
    
    void mergeSort(int a[], int l, int r, int k){
        if(l<r){
            int m = l + (r-l)/2 ;
            mergeSort(a, l, m, k);
            mergeSort(a, m+1, r, k);
            merge(a,l,m,r,k);
        }
    }
    // A[]: input array
    // N: size of array
    //Function to sort the array according to difference with given number.
    void sortABS(int A[],int N, int k)
    {
       //Your code here
       mergeSort(A, 0, N-1, k);
    }
};
```

