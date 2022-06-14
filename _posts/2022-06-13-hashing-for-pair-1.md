---
layout: post
title: Hashing for pair - 1  
summary:
tags:
    - hash
    - array
    - geeksforgeeks
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/hashing-for-pair-1/0/)  

You are given an array of distinct integers and a sum. Check if there's a pair with the given sum in the array.

**Your Task:** 
You don't need to read input or print anything. Your task is to complete the provided function `sumExists ()` which take the array `arr[]`, its size `N`, and an integer `sum` as inputs and returns `1` if there exists a pair with the given sum in the array, else, it returns `0`.


**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input:
N = 10
arr[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10} 
sum = 14
Output: 
1

Explanation: 
arr[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10} 
and sum = 14.  There is a pair {4, 10} 
with sum 14.
```

**Example 2:**   
```
Input:
N = 2
arr[] = {2, 5}
sum = 10
Output:
0

Explanation: 
arr[]  = {2, 5} and sum = 10. 
There is no pair with sum 10.
```

### Constraints

+ `1 <= N <= 10^6`
+ `0 <= arr[i] <= 10^6` 
+ `1 <= sum <= 1000`

## Solutions

```cpp
class Solution{
    public:
    // You need to complete this function.
    // Function to check if there is a pair with the given sum in the array.
    int sumExists(int arr[], int N, int sum) {
        // Your code here.
        unordered_set<int> s;
        for(int i=0; i<N; i++)
            if(s.find(sum-arr[i])!=s.end())
                return 1;
            else s.insert(arr[i]);
        return 0;
    }
};
```

