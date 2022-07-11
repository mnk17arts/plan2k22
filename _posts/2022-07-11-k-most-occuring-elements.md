---
layout: post
title: K Most occurring elements               
summary:
tags:
    - heap
    - priority-queue
    - geeksforgeeks
    - cpp
    - medium
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/most-occurring-elements-1587115620/0/?track=DSASP-Heap&batchId=154)  

Given an array `arr[]` of `N` integers in which elements may be repeating several times. Also, a positive number `K` is given and the task is to find sum of total frequencies of `K` most occurring elements

Note: The value of `K` is guaranteed to be less than or equal to the number of distinct elements in `arr`.

**Your Task:** 
Complete the function `kMostFrequent()` whic returns the frequencies of `K` most occuring elements.



**Expected Time Complexity:** `O(NLogN)`           
**Expected Auxiliary Space:** `O(N)`


### Examples

**Example 1:**   
```
Input:
N = 8
arr[] = {3,1,4,4,5,2,6,1}
K = 2
Output: 4
Explanation: Since, 4 and 1 are 2 most
occurring elements in the array with
their frequencies as 2, 2. So total
frequency is 2 + 2 = 4.
``` 


**Example 2:**   
```
Input:
N = 8
arr[] = {3,3,3,4,1,1,6,1}
K = 2
Output: 6
Explanation: Since, 3 and 1 are most
occurring elements in the array with
frequencies 3, 3 respectively. So,
total frequency is 6.
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
    //Function to return the sum of frequencies of k numbers
    //with most occurrences in an array.
    int kMostFrequent(int arr[], int n, int k) 
    { 
    	// Your code here	
    	unordered_map<int,int> um;
    	for(int i=0;i<n;i++) um[arr[i]]++;
    	
    	priority_queue<int> pq;
    	for(auto i: um)
    	    pq.push(i.second);
    	    
    	int sum=0;
    	while(k--){
    	    sum += pq.top();
    	    pq.pop();
    	}
    	
    	return sum;	
    } 
};
```

