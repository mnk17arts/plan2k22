---
layout: post
title: Nearly sorted                
summary:
tags:
    - heap
    - priority-queue
    - queue
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/nearly-sorted-1587115620/0/?track=DSASP-Heap&batchId=154)  

Given an array of `n` elements, where each element is at most `k` away from its target position, you need to sort the array optimally.

**Your Task:** 
You are required to complete the method `nearlySorted()` which takes 3 arguments and returns the sorted array.
Note: DO NOT use STL `sort()` function for this question.



**Expected Time Complexity:** `O(NLogk)`           
**Expected Auxiliary Space:** `O(N)`


### Examples

**Example 1:**   
```
Input:
n = 7, k = 3
arr[] = {6,5,3,2,8,10,9}
Output: 2 3 5 6 8 9 10
Explanation: The sorted array will be
2 3 5 6 8 9 10
``` 


**Example 2:**   
```
Input:
n = 5, k = 2
arr[] = {3,1,4,2,5}
Output: 1 2 3 4 5 
```


### Constraints

+ `1 <= N <= 10^6`
+ `1 <= K <= 10^6`
+ `1 <= arr[i] <= 10^7`

## Solutions

```cpp
class Solution
{
    public:
    //Function to return the sorted array.
    vector <int> nearlySorted(int arr[], int num, int K){
        // Your code here
        K++;
        priority_queue<int,vector<int>,greater<int>> pq(arr,arr+K);
        for(int i=K; i<num; i++){
            arr[i-K] = pq.top(); pq.pop();
            pq.push(arr[i]);
        }
        for(int i=num-K; i<num; i++){
            arr[i] = pq.top(); pq.pop();
        }
        vector<int> v(arr,arr+num);
        return v;
    }
};
```

