---
layout: post
title: Reverse array in groups
summary:
tags:
    - array
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/reverse-array-in-groups0255/1/)  

Given an array `arr[]` of positive integers of size `N`. Reverse every sub-array group of size `K`.


**Your Task:** 
You don't need to read input or print anything. The task is to complete the function `reverseInGroups()` which takes the array, `N` and `K` as input parameters and modifies the array in-place. 

**Expected Time Complexity**: `O(N)`.     
**Expected Auxiliary Space**: `O(N)`.


### Examples

**Example 1:**   
```
Input:
N = 5, K = 3
arr[] = {1,2,3,4,5}
Output: 3 2 1 5 4
Explanation: First group consists of elements
1, 2, 3. Second group consists of 4,5.
```

**Example 2:**   
```
Input:
N = 4, K = 3
arr[] = {5,6,8,9}
Output: 8 6 5 9
```

### Constraints

+ `1 <= N,K <= 10^7`
+ `1 <= A[i] <= 10^18`

## Solutions

```cpp
class Solution{
public:
    //Function to reverse every sub-array group of size k.
    void reverseInGroups(vector<long long>& arr, int n, int k){
        // code here
        for(int i=0; i<n; i+=k){
            if(i+k < n)
            reverse(arr.begin()+i, arr.begin()+(k+i));
            else
            reverse(arr.begin()+i, arr.end());
        }
    }
};
```

