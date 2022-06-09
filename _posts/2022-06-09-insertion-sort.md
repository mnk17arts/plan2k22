---
layout: post
title: Insertion Sort 
summary:
tags:
    - sorting
    - insertion-sort
    - algorithm
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/insertion-sort/0/#)  

The task is to complete the `insert()` function which is used to implement Insertion Sort.

**Your Task:** 
You don't have to read input or print anything. Your task is to complete the function `insert()` and `insertionSort()` where `insert()` takes the array, it's size and an index `i` and `insertionSort()` uses insert function to sort the array in ascending order using insertion sort algorithm. 


**Expected Time Complexity:** `O(N^N)`  
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
+ `1 <= arr[i] = 10^3` 

## Solutions

```cpp
class Solution{
    public:
    void insert(int arr[], int i){
        // Your code here  
        int key = arr[i];
        int j = i-1;
        for(; j>=0 && (arr[j] > key); j--)
            arr[j+1] = arr[j];
        arr[j+1] = key;
    }
    //Function to sort the array using insertion sort algorithm.
    void insertionSort(int arr[], int n){
        //code here
        for(int i=1; i<n ; i++){
            insert(arr, i);
        }
    }
};
```

