---
layout: post
title: K largest elements             
summary:
tags:
    - heap
    - priority-queue
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/k-largest-elements3736/0/?track=DSASP-Heap&batchId=154#)  

Given an array of `N` positive integers, print `k` largest elements from the array. 


**Your Task:** 
Complete the function `kLargest()` that takes the array, `N` and `K` as input parameters and returns a list of `k` largest element in descending order. 



**Expected Time Complexity:** `O(N * Log(K))`           
**Expected Auxiliary Space:** `O(K)`


### Examples

**Example 1:**   
```
Input:
N = 5, k = 2
arr[] = {12,5,787,1,23}
Output: 787 23
Explanation: First largest element in
the array is 787 and the second largest
is 23.
``` 


**Example 2:**   
```
Input:
N = 7, k = 3
arr[] = {1,23,12,9,30,2,50}
Output: 50 30 23
Explanation: Three Largest element in
the array are 50, 30 and 23.
```


### Constraints

+ `1 <= N <= 10^4`
+ `K <= N`
+ `1 <= arr[i] <= 10^6`

## Solutions

```cpp
class Solution
{
    public:
    //Function to return k largest elements from an array.
    vector<int> kLargest(int arr[], int n, int k)
    {
        // code here
        priority_queue<int, vector<int>, greater<int>> pq(arr,arr+k);
        for(int i=k; i<n; i++) 
            if(pq.top() < arr[i]) { pq.pop(); pq.push(arr[i]); }
        vector<int> v(k);
        for(;k>0;) { v[--k]=pq.top(); pq.pop(); }
        return v;
        
    }
};
```

