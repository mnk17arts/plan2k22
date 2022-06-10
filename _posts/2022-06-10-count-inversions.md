---
layout: post
title: Count Inversions 
summary:
tags:
    - array
    - divide-conquer
    - sorting
    - merge-sort
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/inversion-of-array-1587115620/0/#)  

Given an array of integers. Find the Inversion Count in the array. 

***Inversion Count***: For an array, inversion count indicates how far (or close) the array is from being sorted. If array is already sorted then the inversion count is `0`. If an array is sorted in the reverse order then the inversion count is the maximum. 
Formally, two elements `a[i]` and `a[j]` form an inversion if `a[i] > a[j]` and `i < j`.

**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `inversionCount()` which takes the array `arr[]` and the size of the array as inputs and returns the inversion count of the given array.


**Expected Time Complexity:** `O(NlogN)`  
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input: N = 5, arr[] = {2, 4, 1, 3, 5}
Output: 3
Explanation: The sequence 2, 4, 1, 3, 5 
has three inversions (2, 1), (4, 1), (4, 3).
```

**Example 2:**   
```
Input: N = 5
arr[] = {2, 3, 4, 5, 6}
Output: 0
Explanation: As the sequence is already 
sorted so there is no inversion count.
```

**Example 3:**   
```
Input: N = 3, arr[] = {10, 10, 10}
Output: 0
Explanation: As all the elements of array 
are same, so there is no inversion count.
```

### Constraints

+ `1 <= N <= 5*10^5`
+ `1 <= arr[i] = 10^18` 

## Solutions

```cpp
class Solution{
    public:
    // arr[]: Input Array
    // N : Size of the Array arr[]
    // Function to count inversions in the array.
    long long int merge(long long arr[], long long left, long long mid, long long right){
        long long count = 0;
        long long n1 = mid - left + 1, n2 = right - mid;
        long long L[n1] , R[n2];
        for(long long i=0; i<n1; i++)
            L[i] = arr[left+i];    
        for(long long int i=0; i<n1; i++)
            R[i] = arr[mid+1+i];
        long long int i=0, j=0, k=left;
        while( i < n1 && j < n2){
            if(L[i] <= R[j]){
                arr[k] = L[i];  
                i++;
            }
            else{
                arr[k] = R[j];
                count += n1 - i;
                j++;
            } 
            k++;
        }
        while( i < n1){
            arr[k] = L[i];
            k++, i++;
        }
    
        while( j < n2){
            arr[k] = R[j];  
            k++, j++;
        }
    
        return count;
        
    }
    
    long long inversionCountx(long long arr[], long long left, long long right){
        long long count = 0, mid;
        if(left < right){
            mid = (right + left)/2 ;
            count += inversionCountx(arr, left, mid);
            count += inversionCountx(arr, mid+1, right);
            count += merge(arr, left, mid, right);
        }
        return count;
    }
    
    long long inversionCount(long long arr[], long long N){
        // Your Code Here
        return inversionCountx(arr, 0, N-1);
    }
};
```

