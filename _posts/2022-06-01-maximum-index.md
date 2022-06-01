---
layout: post
title: Maximum Index  
summary:
tags:
    - array
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/maximum-index-1587115620/1/#)  

Given an array `A[]` of `N` positive integers. The task is to find the maximum of `j - i` subjected to the constraint of `A[i] < A[j]` and `i < j`.

**Your Task:** 
The task is to complete the function `maxIndexDiff()` which finds and returns maximum index difference. Printing the output will be handled by driver code. Return `-1` in case no such index is found. 

**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input:
N = 2
A[] = {1, 10}
Output:
1
Explanation:
A[0]<A[1] so (j-i) is 1-0 = 1.
```

**Example 2:**   
```
Input:
N = 9
A[] = {34, 8, 10, 3, 2, 80, 30, 33, 1}
Output:
6
Explanation:
In the given array A[1] < A[7]
satisfying the required 
condition(A[i] < A[j]) thus giving 
the maximum difference of j - i 
which is 6(7-1).
```

### Constraints

+ `1 <= N <= 10^7`
+ `0 ≤ A[i] <= 10^9`

## Solutions

```cpp
class Solution{
    public:
         
    // A[]: input array
    // N: size of array
    // Function to find the maximum index difference.
    int maxIndexDiff(int A[], int n) 
    { 
        int lmn[n] , rmx[n];
        lmn[0] = A[0];
        rmx[n-1] = A[n-1];
        for(int i=1; i<n; i++)
            lmn[i] = min(A[i], lmn[i-1]);
        for(int i=n-2; i>=0; i--)
            rmx[i] = max(A[i], rmx[i+1]);
        int i=0, j=0, res=-1;
        while(i<n && j<n){
            if(lmn[i] <= rmx[j]){
                res = max(res, j-i);
                j++;
            }else
                i++;
        }
        return res;
    }
};
```

