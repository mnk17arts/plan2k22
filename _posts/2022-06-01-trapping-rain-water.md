---
layout: post
title:  Trapping Rain Water 
summary:
tags:
    - array
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/trapping-rain-water-1587115621/1/)  

Given an array `arr[]` of `N` non-negative integers representing the height of blocks. If width of each block is `1`, compute how much water can be trapped between the blocks during the rainy season. 
 
**Your Task:** 
You don't need to read input or print anything. The task is to complete the function `trappingWater()` which takes `arr[]` and `N` as input parameters and returns the total amount of water that can be trapped.

**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input:
N = 6
arr[] = {3,0,0,2,0,4}
Output:
10
Explanation: 
Bars for input {3, 0, 0, 2, 0, 4} Total trapped water = 3 +3 +1+3=10
```

**Example 2:**   
```
Input:
N = 4
arr[] = {7,4,0,9}
Output:
10
Explanation:
Water trapped by above 
block of height 4 is 3 units and above 
block of height 0 is 7 units. So, the 
total unit of water trapped is 10 units.
```

**Example 3:**   
```
Input:
N = 3
arr[] = {6,9,9}
Output:
0
Explanation:
No water will be trapped.
```

### Constraints

+ `3 <= N <= 10^6`
+ `0 ≤ A[i] <= 10^8`

## Solutions

```cpp
class Solution{
    // Function to find the trapped water between the blocks.
    public:
    long long trappingWater(int arr[], int n){
        // code here
        int lft[n], rgt[n];
        lft[0] = arr[0];
        rgt[n-1] = arr[n-1];
        for(int i = 1; i<n; i++)
            lft[i] = max(arr[i], lft[i-1]);
        for(int i=n-2; i>=0; i--)
            rgt[i] = max(arr[i], rgt[i+1]);
        long long res = 0;
        for(int i=1; i<n-1; i++)
            res += min(lft[i],rgt[i])-arr[i] ;
        return res;
        
    }
};
```

