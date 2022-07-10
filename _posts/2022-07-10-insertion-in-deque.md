---
layout: post
title:  Insertion in deque               
summary:
tags:
    - deque
    - geeksforgeeks
    - cpp
    - easy
minute: 1 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/insertion-in-deque/0/?track=DSASP-Deque&batchId=154#)  

Given an array `arr[]` of size `N` containing non-negative integers. You need to insert all elements of the array to deque and return it.


**Your Task:** 
You need to complete the function `deque_Init()` which takes array `arr[]` and it's size `N` as input parameters and should return deque that contains array elements. You don't have to worry about input.


**Expected Time Complexity:** `O(N)`            
**Expected Auxiliary Space:** `O(1)` 


### Examples

**Example 1:**   
```
Input: 
5
1 2 3 4 5

Output: 
1 2 3 4 5

Explanation: 
After insert in the deque 
it will look like {1, 2, 3, 4, 5}. 
```


**Example 2:**   
```
Input:
1
1

Output: 
1

Explanation: 
After insert in the deque 
it will look like {1}.
```


### Constraints

+ `1 <= N <= 10^5`

## Solutions

```cpp
class Solution {
  public:
    // Function to insert all elements of the array in deque.
    deque<int> deque_Init(int arr[], int n) {
        // add your code here
        deque<int> d({arr,arr+n});
        return d;
    }
};
```

