---
layout: post
title: Subarray with given sum 
summary:
tags:
    - slidingwindow
    - searching
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/subarray-with-given-sum-1587115621/1/)  

Given an unsorted array `A` of size `N` that contains only non-negative integers, find a continuous sub-array which adds to a given number `S`.

In case of multiple subarrays, return the subarray which comes first on moving from left to right.

**Note:** Return `-1` if a valid assignment is not possible, and allotment should be in contiguous order (see the explanation for better understanding).

**Your Task:** 
You don't need to read input or print anything. The task is to complete the function `subarraySum()` which takes arr, N and S as input parameters and returns an `arraylist` containing the `starting` and `ending` positions of the first such occurring subarray from the left where sum equals to S. The two indexes in the array should be according to 1-based indexing. If no such subarray is found, return an array consisting only one element that is `-1`.

**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
N = 5, S = 12
A[] = {1,2,3,7,5}
Output: 2 4
Explanation: The sum of elements 
from 2nd position to 4th position 
is 12.
```

**Example 2:**   
```
Input:
N = 10, S = 15
A[] = {1,2,3,4,5,6,7,8,9,10}
Output: 1 5
Explanation: The sum of elements 
from 1st position to 5th position
is 15.
```

### Constraints

+ `1 <= N <= 10^5`
+ `1 <= arr[i] = 10^9` 

## Solutions

```cpp
class Solution{
    public:
    //Function to find a continuous sub-array which adds up to a given number.
    vector<int> subarraySum(int arr[], int n, long long s){
        vector<int> ans;
        int start=0, end=0;
        long long sum=0;
        while(end <= n && start <= n){
            if(sum==s){
                ans.push_back(start+1);
                ans.push_back(end);
                return ans;
            }
            else if(sum < s)
                sum += arr[end++];
            if(sum > s)
                sum -= arr[start++];
        }
        return {-1};
    }
};
```

