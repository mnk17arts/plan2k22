---
layout: post
title: Kth largest element in a stream               
summary:
tags:
    - heap
    - priority-queue
    - geeksforgeeks
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/kth-largest-element-in-a-stream-1587115620/0/?track=DSASP-Heap&batchId=154)  

Given an input stream of n integers, find the kth largest element each time when an new element is added to the stream.

**Your Task:** 
You are required to complete the method `kthLargest()` which takes `3` arguments and prints `k`th largest element else -1.




**Expected Time Complexity:** `O(N * Log(K))`           
**Expected Auxiliary Space:** `O(K)`


### Examples

**Example 1:**   
```
Input:
k = 4, n = 6
arr[] = {1,2,3,4,5,6}
Output: -1 -1 -1 1 2 3
Explanation: k = 4
For 1, the 4th largest element doesn't
exist so we print -1.
For 2, the 4th largest element doesn't
exist so we print -1.
For 3, the 4th largest element doesn't
exist so we print -1.
For 4, the 4th largest element is 1
{1, 2, 3, 4}
For 5, the 4th largest element is 2
{2, 3, 4 ,5}
For 6, the 4th largest element is 3
{3, 4, 5, 6}
``` 


**Example 2:**   
```
Input:
k = 1, n = 2
arr[] = {3,4}
Output: 3 4 
```


### Constraints

+ `1 <= N <= 10^6`
+ `1 <= K <= N`
+ `1 <= arr[i] <= 10^5`

## Solutions

```cpp
class Solution
{
    public:
    //Function to print kth largest element for each element in the stream.
    void kthLargest(int arr[], int n, int k)
    {
    	// your code here
        priority_queue<int, vector<int>, greater<int>> pq(arr,arr+k);
        for(int i=1; i<k; i++) cout<<-1<<" ";
        for(int i=k; i<n; i++) {
            cout << pq.top() << " ";
            if(pq.top() < arr[i]) { pq.pop(); pq.push(arr[i]); }  

        }
        cout<<pq.top()<< " ";
    }
};
```

