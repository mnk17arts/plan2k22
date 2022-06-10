---
layout: post
title: Find triplets with zero sum
summary:
tags:
    - array
    - sorting
    - searching
    - 2pointers
    - geeksforgeeks
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/find-triplets-with-zero-sum/0/#)  

Given an array `arr[]` of `n` integers. Check whether it contains a triplet that sums up to zero. 

**Your Task:** 
You don't need to read input or print anything. Your task is to complete the boolean function `findTriplets()` which takes the array `arr[]` and the size of the `array (n)` as inputs and print `1` if the function returns true else print `0` if the function returns `false`. 

**Expected Time Complexity:** `O(n^2)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input: n = 5, arr[] = {0, -1, 2, -3, 1}
Output: 1
Explanation: 0, -1 and 1 forms a triplet
with sum equal to 0.
```

**Example 2:**   
```
Input: n = 3, arr[] = {1, 2, 3}
Output: 0
Explanation: No triplet with zero sum exists. 
```

### Constraints

+ `1 <= n <= 10^4`
+ `-10^6 <= arr[i] = 10^6` 

## Solutions

```cpp
class Solution{
    public:
    //Function to find triplets with zero sum.
    bool findTriplets(int arr[], int n)
    { 
        //Your code here
        sort(arr, arr+n);
        for(int i=n-1; i>=2; i-- ){
            int l = 0, h = i-1;
            int t = -arr[i];
            while(l<h){
                if(arr[l]+arr[h] == t) return 1;
                else if(arr[l] + arr[h] < t) l++;
                else h--;
            }
        }
        return 0; 
    }
};
```

