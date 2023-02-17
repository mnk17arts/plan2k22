---
layout: post
title: Find duplicates in an array
summary:
tags:
  - geeksforgeeks
  - array
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/find-duplicates-in-an-array/1)

Given an array a[] of size N which contains elements from 0 to N-1, you need to find all the elements occurring more than once in the given array.

Note: The extra space is only for the array to be returned.
Try and perform all operations within the provided array. 

**Your Task:**

Complete the function duplicates() which takes array a[] and n as input as parameters and returns a list of elements that occur more than once in the given array in a sorted manner. If no such element is found, return list containing [-1]. 



**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**

```
Input:
N = 4
a[] = {0,3,1,2}
Output: -1
Explanation: N=4 and all elements from 0
to (N-1 = 3) are present in the given
array. Therefore output is -1.
```

**Example 2:**

```
Input:
N = 5
a[] = {2,3,1,2,3}
Output: 2 3 
Explanation: 2 and 3 occur more than once
in the given array.
```

### Constraints

- `1 <= N < 10^5`
- `0 <= arr[i] < N-1`

## Solutions

```cpp

class Solution{
  public:
    vector<int> duplicates(int arr[], int n) {
        // code here
        vector<int> temp(n,0), res;
        for(int i = 0; i < n; i++) {
            temp[arr[i]]++;
        }
        for(int i = 0; i < n; i++) {
            if(temp[i] > 1) {
                res.push_back(i);
            }
        }
        if(res.size() == 0) {
            res.push_back(-1);
        }
        return res;
        
    }
};

```
