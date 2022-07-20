---
layout: post
title: Print first n Fibonacci Numbers                      
summary:
tags:
    - dynamic-programming
    - geeksforgeeks
    - cpp
    - easy
minute: 1 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/print-first-n-fibonacci-numbers1002/0/?track=DSASP-DP&batchId=154)  

Given a number `N`, find the first `N` Fibonacci numbers. The first two number of the series are `1` and `1`.

**Your Task:** 

Your task is to complete `printFibb()` which takes single argument `N` and returns a list of first `N` Fibonacci numbers.


**Expected Time Complexity:** `O(N)`              
**Expected Auxiliary Space:** `O(N)`
Note: This space is used to store and return the answer for printing purpose.


### Examples

**Example 1:**   
```
Input:
N = 5
Output: 1 1 2 3 5
```

**Example 2:**   
```
Input:
N = 7
Output: 1 1 2 3 5 8 13
```

### Constraints

+ `1 ≤ N <= 84`


## Solutions

```cpp
class Solution
{
    public:
    //Function to return list containing first n fibonacci numbers.
    vector<long long> printFibb(int n) 
    {
        //code here
        vector<long long> v(n);
        v[0]=1,v[1]=1;
        for(int i=2;i<n;i++)
            v[i]=v[i-1]+v[i-2];
        return v;
    }
};
```

