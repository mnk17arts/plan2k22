---
layout: post
title: Check if two arrays are equal or not 
summary:
tags:
    - hash
    - array
    - sorting
    - geeksforgeeks
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/check-if-two-arrays-are-equal-or-not3847/0/)  

Given two arrays `A` and `B` of equal size `N`, the task is to find if given arrays are equal or not. Two arrays are said to be equal if both of them contain same set of elements, arrangements (or permutation) of elements may be different though.
Note : If there are repetitions, then counts of repeated elements must also be same for two array to be equal.

**Your Task:** 
Complete `check()` function which takes both the given array and their size as function arguments and returns `true` if the arrays are equal else returns `false`.The `0` and `1` printing is done by the driver code.


**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input:
N = 5
A[] = {1,2,5,4,0}
B[] = {2,4,5,0,1}
Output: 1
Explanation: Both the array can be 
rearranged to {0,1,2,4,5}
```

**Example 2:**   
```
Input:
N = 3
A[] = {1,2,5}
B[] = {2,4,15}
Output: 0
Explanation: A[] and B[] have only 
one common value.
```

### Constraints

+ `1 <= N <= 10^7`
+ `1 <= A[i],B[i] <= 10^18` 

## Solutions

```cpp
class Solution{
    public:
    //Function to check if two arrays are equal or not.
    bool check(vector<ll> A, vector<ll> B, int N) {
        //code here
        unordered_map<int, int> m;
        for(int i=0; i<N; i++){
            m[A[i]]++;
            m[B[i]]--;
        }
        for(auto i: m)
            if(i.second)
                return false;
        return true;
    }
};
```

