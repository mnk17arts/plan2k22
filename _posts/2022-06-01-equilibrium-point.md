---
layout: post
title: Equilibrium Point  
summary:
tags:
    - array
    - prefix-sum
    - geeksforgeeks
    - cpp
    - easy
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/equilibrium-point-1587115620/1#)  

Given an array `A` of `n` positive numbers. The task is to find the first Equilibium Point in the array. 
Equilibrium Point in an array is a position such that the sum of elements before it is equal to the sum of elements after it.

**Note: Retun the index of Equilibrium point. (1-based index)**


**Your Task:** 
The task is to complete the function `equilibriumPoint()` which takes the array and `n` as input parameters and returns the point of equilibrium. Return `-1` if no such point exists.

**Expected Time Complexity:** `O(n)`  
**Expected Auxiliary Space:** `O(1)`   

### Examples

**Example 1:**   
```
Input: 
n = 5 
A[] = {1,3,5,2,2} 
Output: 3 
Explanation: For second test case 
equilibrium point is at position 3 
as elements before it (1+3) = 
elements after it (2+2). 
```

**Example 2:**   
```
Input:
n = 1
A[] = {1}
Output: 1
Explanation:
Since its the only element hence
its the only equilibrium point.
```

### Constraints

+ `1 <= n <= 10^6`
+ `1 ≤ A[i] <= 10^8`

## Solutions

```cpp
class Solution{
    public:
    // Function to find equilibrium point in the array.
    // a: input array
    // n: size of array
    int equilibriumPoint(long long a[], int n) {
    
        // Your code here
        int rsum = a[0];
        for(int i=1; i<n; i++) rsum+=a[i];
        int lsum = 0; 
        for(int i=0; i<n; i++){
            rsum -= a[i];
            if(lsum == rsum) 
            return i+1;
            lsum += a[i];
        }
        return -1;
    }
};
```

