---
layout: post
title: Strongest Neighbour 
summary:
tags:
    - array
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/max-and-second-max/1/)  

Given an array `arr[]` of `n` positive integers. The task is to find the maximum for every adjacent pairs in the array.


**Your Task:** 
The task is to complete the function `maximumAdjacent()`, which takes `sizeOfArray (n)` and `array(arr)` as parameters and prints the maximum of all adjacent pairs (space separated).

**Expected Time Complexity**: `O(N)`.     
**Expected Auxiliary Space**: `O(1)`.


### Examples

**Example 1:**   
```
Input:
n = 6
arr[] = {1,2,2,3,4,5}
Output: 2 2 3 4 5
Explanation: Maximum of arr[0] and arr[1]
is 2, that of arr[1] and arr[2] is 2, ...
and so on. For last two elements, maximum 
is 5.
```

**Example 2:**   
```
Input:
n = 2
arr[] = {5, 5}
Output: 5
Explanation: We only have two elements 
so max of 5 and 5 is 5 only.
```

### Constraints

+ `2 <= N <= 10^6`
+ `1 <= arr[i] <= 10^6`

## Solutions

```cpp
// Function to find maximum for every adjacent pairs in the array.
void maximumAdjacent(int sizeOfArray, int arr[]){
    
    /*******************************************
     * Your code here
     * Function should print max adjacents for all pairs
     ********************************************/
     for(int i=0; i<sizeOfArray-1; i++)
        cout << max(arr[i], arr[i+1]) << " ";
    
}
```

