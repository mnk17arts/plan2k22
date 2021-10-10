---
layout: post
title: Valid Pair Sum
description: 
summary: 
tags:
    - array
    - geeksforgeeks
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/3b76f77c1b2107f809b1875aa9fe929ce320be97/1#)
Given an array of size `N`, find the number of distinct pairs `{i, j}` (`i != j`) in the array such that the sum of `a[i]` and `a[j]` is greater than `0`.


### Examples
**Example 1:**  
```
Input: N = 3, a[] = {3, -2, 1}
Output: 2
Explanation: {3, -2}, {3, 1} are two 
possible pairs.
```

**Example 2:**  
```
Input: N = 4, a[] = {-1, -1, -1, 0}
Output: 0
Explanation: There are no possible pairs.
```

**Example 3:**  
```
Input: nums1 = [1,2,2], nums2 = [4,3,3], nums3 = [5]
Output: []
Explanation: No value is present in at least two arrays.
```

### Constraints
+ `1 ≤ N ≤ 10^5` 
+ `-10^4  ≤ a[i] ≤ 10^4`

**Expected Time Complexity**: `O(N * Log(N))`    
**Expected Auxiliary Space:** `O(1)`

## Solutions
```cpp
class Solution{
    public:
    long long ValidPair(int a[], int n) 
    { 
        sort(a,a+n);
        int l=0,r=n-1;
        long long ans = 0;
        while(l!=r){
            if(a[l]+a[r]>0){
                ans+=(r-l);
                r--;
            }else if(a[l]+a[r]<=0) l++;
        }
        return ans;
    }   
};
```
