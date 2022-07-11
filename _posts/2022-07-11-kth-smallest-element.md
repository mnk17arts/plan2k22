---
layout: post
title: Kth smallest element              
summary:
tags:
    - heap
    - priority-queue
    - geeksforgeeks
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/kth-smallest-element5545-1587115620/0/?track=DSASP-Heap&batchId=154)  

Given an array `arr[]` of `N` positive integers and a number `K`. The task is to find the `k`th smallest element in the array.

**Your Task:** 
You  don't need to read inputs or print anything. Complete the method `kthSmallest()` which takes array `arr[]`, size of the array `n` and value `k` as input parameters and returns kth smallest element.




**Expected Time Complexity:** `O(N * Log(K))`           
**Expected Auxiliary Space:** `O(K)`


### Examples

**Example 1:**   
```
Input: 
N = 5, K = 3
arr[] = {3,5,4,2,9}

Output: 
4

Explanation: 
Third smallest element in the array is 4.
``` 


**Example 2:**   
```
Input:
N = 5, k = 5
arr[] = {4,3,7,6,5}

Output: 
7

Explanation: 
Fifth smallest element in the array is 7.
```


### Constraints

+ `1 <= N <= 10^6`
+ `1 <= K <= N`
+ `1 <= arr[i] <= 10^6`
Array do not contains duplicates.

## Solutions

```cpp
class Solution
{
    public:
    //Function to find the kth smallest element in the array.
    int kthSmallest(int arr[], int n, int k)
    {
        // Your code here
        priority_queue<int> pq(arr,arr+k);
        for(int i=k; i<n; i++)
            if(pq.top() > arr[i]) { pq.pop(); pq.push(arr[i]); }
        return pq.top();
    }
};
```

