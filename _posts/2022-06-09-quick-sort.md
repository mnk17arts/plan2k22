---
layout: post
title: Quick Sort 
summary:
tags:
    - sorting
    - quick-sort
    - divide-conquer
    - algorithm
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/quick-sort/0/)  

Quick Sort is a Divide and Conquer algorithm. It picks an element as pivot and partitions the given array around the picked pivot.
Given an array `arr[]`, its starting position low and its ending position high.

Implement the `partition()` and `quickSort()` functions to sort the array.



**Your Task:** 
You don't need to read input or print anything. Your task is to complete the functions `partition()`  and `quickSort()` which takes the array arr[], low and high as input parameters and partitions the array. Consider the last element as the pivot such that all the elements less than(or equal to) the pivot lie before it and the elements greater than it lie after the pivot. 


**Expected Time Complexity:** `O(N^logN)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input: 
N = 5
arr[] = {4, 1, 3, 9, 7}
Output: 
1 3 4 7 9
```

**Example 2:**   
```
Input:
N = 10 
arr[] = {10, 9, 8, 7, 6, 5, 4, 3, 2, 1}
Output: 
1 2 3 4 5 6 7 8 9 10
```

### Constraints

+ `1 <= N <= 10^3`
+ `1 <= arr[i] = 10^4` 

## Solutions

```cpp
class Solution{
    public:
    //Function to sort an array using quick sort algorithm.
    void quickSort(int arr[], int low, int high){
        // code here
        if(low < high){
            int pi = partition(arr, low, high);
            quickSort(arr,low, pi-1);
            quickSort(arr,pi+1, high);
        }
        
    }
    
    public:
    int partition (int arr[], int low, int high){
       // Your code here
       int i = low - 1;
       int pivot = arr[high];
       for(int j=low; j<high; j++){
           if(arr[j] < pivot){
               i++;
               swap(arr[i],arr[j]);
           }
       }
       swap(arr[i+1],arr[high]);
       return i+1;
    }
};
```

