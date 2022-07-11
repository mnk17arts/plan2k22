---
layout: post
title: Kth largest element              
summary:
tags:
    - heap
    - priority-queue
    - geeksforgeeks
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/kth-largest-element5034/0/?track=DSASP-Heap&batchId=154#)  

Given an array `arr[]` of `N` positive integers and a number `K`. The task is to find the `k`th largest element in the array.

**Your Task:** 
You are required to complete the method `KthLargest()` which takes `3` arguments and returns the `K`th Largest element. 



**Expected Time Complexity:** `O(N * Log(K))`           
**Expected Auxiliary Space:** `O(K)`


### Examples

**Example 1:**   
```
Input:
N = 5, K = 3
arr[] = {3, 5, 4, 2, 9}
Output: 
4
Explanation: 
Third largest element
in the array is 4.
``` 


**Example 2:**   
```
Input:
N = 5, K = 5
arr[] = {4, 3, 7, 6, 5} 
Output: 
3
Explanation: 
Fifth largest element
in the array is 3.
```


### Constraints

+ `1 <= N <= 10^6`
+ `1 <= K <= N`
+ `1 <= arr[i] <= 10^6`

## Solutions

```cpp
class Solution
{
    public:
    //Function to return kth largest element from an array.
    int KthLargest(int arr[], int n, int k) {
        // Your code here
        priority_queue<int, vector<int>, greater<int>> pq(arr,arr+k);
        for(int i=k; i<n; i++) 
            if(pq.top() < arr[i]) { pq.pop(); pq.push(arr[i]); }
        return pq.top();
    }
};
```

