---
layout: post
title: Floor in a Sorted Array
summary:
tags:
    - array
    - binary-search
    - searching
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/floor-in-a-sorted-array-1587115620/1/#)  

Given a sorted array `arr[]` of size `N` without duplicates, and given a value `x`. Floor of `x` is defined as the largest element `K` in `arr[]` such that `K` is smaller than or equal to `x`. Find the index of `K`(0-based indexing).

**Your Task:** 
The task is to complete the function `findFloor()` which returns an integer denoting the index value of `K` or return `-1` if there isn't any such number.

**Expected Time Complexity:** `O(logN)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
N = 7, x = 0 
arr[] = {1,2,8,10,11,12,19}
Output: -1
Explanation: No element less 
than 0 is found. So output 
is "-1".

```

**Example 2:**   
```
Input:
N = 7, x = 5 
arr[] = {1,2,8,10,11,12,19}
Output: 1
Explanation: Largest Number less than 5 is
2 (i.e K = 2), whose index is 1(0-based 
indexing).
```

### Constraints

+ `1 <= N <= 10^7`
+ `1 <= arr[i] = 10^18`
+ `0 <= X <= arr[N-1]`

## Solutions

```cpp
class Solution{
    public:
    // Function to find floor of x
    // n: size of vector
    // x: element whose floor is to find
    int findFloor(vector<long long> v, long long n, long long x){
        
        // Your code here
        int left = 0, right = n-1, ans = -1;
        while(left <= right){
            int mid = left + (right - left)/2 ;
            if(v[mid] == x) return mid;
            else if( v[mid] > x) right = mid - 1;
            else{
                ans = mid;
                left = mid + 1;
            }
        }
        
        return v[ans] <= x ? ans : -1;
    }
};
```

