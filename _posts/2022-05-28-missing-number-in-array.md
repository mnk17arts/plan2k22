---
layout: post
title: Missing number in array 
summary:
tags:
    - arrays
    - bit-manipulation
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/missing-number-in-array1416/1#)  

Given an array of size N-1 such that it only contains distinct integers in the range of 1 to N. Find the missing element.

**Your Task:** 
You don't need to read input or print anything. Complete the function `MissingNumber()` that takes array and `N` as input  parameters and returns the value of the missing number.

**Expected Time Complexity**: ` O(N)`.   
**Expected Auxiliary Space:**   `O(1)`.


### Examples

**Example 1:**   
```
Input:
N = 5
A[] = {1,2,3,5}
Output: 4
```

**Example 2:**   
```
Input:
N = 10
A[] = {6,1,2,8,3,4,7,10,5}
Output: 9
```

### Constraints

+ `1 <= N <= 10^6`
+ `1 <= A[i] <= 10^6`

## Solutions

```cpp
class Solution
{
    public:
   int MissingNumber(vector<int>& array, int n) {
        // Your code goes here
        int res = n;
        for(int i=1; i<n; i++)
            res ^=(i ^ array[i-1]);
        return res;
        
    }
};
```

