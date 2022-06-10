---
layout: post
title: Intersection of two sorted arrays 
summary:
tags:
    - array
    - sorting
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/intersection-of-two-sorted-array-1587115620/0/#)  

The intersection of two arrays contains the elements common to both the arrays. The intersection should not count duplicate elements.
Given two sorted arrays `arr1[]` and `arr2[]` of sizes `N` and `M` respectively. Find their intersection

**Your Task:** 
You do not need to read input or print anything. Complete the function `printIntersection()` that takes `arr1,arr2,  N` and `M` as input parameters and return a list of integers containing the intersection of two arrays. 

**Expected Time Complexity:** `O(n + m)`  
**Expected Auxiliary Space:** `O(min(n,m))`

### Examples

**Example 1:**   
```
Input: 
N = 4, arr1[] = {1, 2, 3, 4}  
M = 5, arr2 [] = {2, 4, 6, 7, 8}
Output: 2 4
Explanation: 2 and 4 are only common 
elements in both the arrays.
```

**Example 2:**   
```
Input: 
N = 5, arr1[] = {1, 2, 2, 3, 4}
M = 6, arr2[] = {2, 2, 4, 6, 7, 8}
Output: 2 4
Explanation: 2 and 4 are the only 
common elements.
```

### Constraints

+ `1 <= n,m <= 10^5`
+ `1 <= arr[i], brr[i] = 10^6` 

## Solutions

```cpp
class Solution{
    public:
    //Function to return a list containing the intersection of two arrays.
    vector<int> printIntersection(int arr1[], int arr2[], int N, int M) 
    { 
        //Your code here
        vector<int> res;
        int i = 0, j =0;
        while( i < N && j < M ){
            if(i > 0 && arr1[i] == arr1[i-1]) { i++; continue;}
            if(j > 0 && arr2[j] == arr2[j-1]) { j++; continue;}
            if(arr1[i]==arr2[j]) {
                res.push_back(arr1[i]);
                i++; j++;
            }
            else if(arr1[i] > arr2[j]) j++;
            else i++;
        }
        return res;
    }
};
```

