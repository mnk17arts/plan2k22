---
layout: post
title: Bubble Sort 
summary:
tags:
    - sorting
    - bubble-sort
    - algorithm
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/bubble-sort/0/#)  

Given an Integer N and a list arr. Sort the array using bubble sort algorithm.

**Your Task:** 
You don't have to read input or print anything. Your task is to complete the function `bubblesort()` which takes the array and it's size as input and sorts the array using bubble sort algorithm.


**Expected Time Complexity:** `O(N^2)`  
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
    //Function to sort the array using bubble sort algorithm.
    void bubbleSort(int arr[], int n)
    {
        // Your code here  
        for(int i=0; i<n; i++){
            bool swapped = false;
            for(int j=0; j< n-i-1; j++)
                if(arr[j] > arr[j+1]){
                    swap(&arr[j],&arr[j+1]);
                    swapped = true;
                }
                    
            if(!swapped)
                break;
        }
    }
};
```

