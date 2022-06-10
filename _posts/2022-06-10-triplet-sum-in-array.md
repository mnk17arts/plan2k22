---
layout: post
title: Triplet Sum in Array 
summary:
tags:
    - sorting
    - array
    - 2pointers
    - geeksforgeeks
    - cpp
    - medium
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/triplet-sum-in-array-1587115621/0/#)  

Given an array arr of size `n` and an integer `X`. Find if there's a triplet in the array which sums up to the given integer `X`.


**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `find3Numbers()` which takes the array `arr[]`, the size of the array (`n`) and the sum (`X`) as inputs and returns `True` if there exists a triplet in the array `arr[]` which sums up to `X` and `False` otherwise.

**Expected Time Complexity:** `O(N^2)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
n = 6, X = 13
arr[] = [1 4 45 6 10 8]
Output:
1
Explanation:
The triplet {1, 4, 8} in 
the array sums up to 13.
```

**Example 2:**   
```
Input:
n = 5, X = 10
arr[] = [1 2 4 3 6]
Output:
1
Explanation:
The triplet {1, 3, 6} in 
the array sums up to 10.
```

### Constraints

+ `1 <= N <= 10^3`
+ `1 <= A[i] <= 10^5`

## Solutions

```cpp
class Solution{
    public:
    //Function to find if there exists a triplet in the 
    //array A[] which sums up to X.
    bool find3Numbers(int A[], int n, int X)
    {
        //Your Code Here
        sort(A, A+n);
        for(int i=n-1; i>=2; i--){
            int rhs = X - A[i];
            int a = 0, b = i-1;
            while(a < b)
                if(A[a] + A[b] == rhs) return true;
                else if( A[a] + A[b] > rhs) b--;
                else a++;
        }
        return false;
    }

};
```

