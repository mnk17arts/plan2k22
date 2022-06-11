---
layout: post
title: Union of Two Sorted Arrays
summary:
tags:
    - array
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/union-of-two-sorted-arrays-1587115621/0/)  

Union of two arrays can be defined as the common and distinct elements in the two arrays.
Given two sorted arrays of size `n` and `m` respectively, find their union.

**Your Task:** 
You do not need to read input or print anything. Complete the function `findUnion()` that takes two arrays `arr1[]`, `arr2[]`, and their size `n` and `m` as input parameters and returns a list containing the union of the two arrays. 


**Expected Time Complexity:** `O(n + m)`  
**Expected Auxiliary Space:** `O(n + m)`

### Examples

**Example 1:**   
```
Input: 
n = 5, arr1[] = [1, 2, 3, 4, 5]  
m = 3, arr2 [] = [1, 2, 3]
Output: 1 2 3 4 5
Explanation: Distinct elements including 
both the arrays are: 1 2 3 4 5.
```

**Example 2:**   
```
Input: 
n = 5, arr1[] = [2, 2, 3, 4, 5]  
m = 5, arr2[] = [1, 1, 2, 3, 4]
Output: 1 2 3 4 5
Explanation: Distinct elements including 
both the arrays are: 1 2 3 4 5.
```

**Example 3:**   
```
Input:
n = 5, arr1[] = [1, 1, 1, 1, 1]
m = 5, arr2[] = [2, 2, 2, 2, 2]
Output: 1 2
Explanation: Distinct elements including 
both the arrays are: 1 2.
```

### Constraints

+ `1 <= n,m <= 10^5`
+ `1 <= arr[i], brr[i] = 10^6` 

## Solutions

```cpp
class Solution{
    public:
    //arr1,arr2 : the arrays
    // n, m: size of arrays
    //Function to return a list containing the union of the two arrays. 
    vector<int> findUnion(int arr1[], int arr2[], int n, int m)
    {
        //Your code here
        //return vector with correct order of elements
        vector<int> res;
        int i=0, j=0;
        while( i < n && j < m){
            if(i > 0 && arr1[i] == arr1[i-1]) { i++; continue ; }
            if(j > 0 && arr2[j] == arr2[j-1]) { j++; continue ; }
            if(arr1[i] == arr2[j]) {res.push_back(arr1[i++]); j++;}
            else if(arr1[i] > arr2[j]) res.push_back(arr2[j++]);
            else res.push_back(arr1[i++]);
        }
        while( i < n ){
            if(arr1[i] == arr1[i-1]) { i++; continue ; }
            res.push_back(arr1[i++]);
        }

        while( j < m ){
            if(arr2[j] == arr2[j-1]) { j++; continue ; }
            res.push_back(arr2[j++]);            
        }

        return res;
    }
};
```

