---
layout: post
title: Count only Repeated
summary:
tags:
    - array
    - searching
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/count-only-repeated2047/1/)  

Given an array `arr[]` of `N` positive integers, where elements are consecutive (sorted). Also, there is a single element which is repeating `X` (any variable) number of times. Now, the task is to find the element which is repeated and number of times it is repeated.
**Note:** If there's no repeating element, Return `{-1,-1}`.

**Your Task:** 
Complete `findRepeating` function and return pair of element which is repeated and the number of times it is repeated. The printing is done by the driver code.

**Expected Time Complexity:** `O(logN)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
N = 5
arr[] = {1,2,3,3,4}
Output: 3 2
Explanation: In the given array, 3 is 
occuring two times.
```

**Example 2:**   
```
Input:
N = 5
arr[] = {2,3,4,5,5}
Output: 5 2
Explanation: In the given array, 5 is 
occuring two times.
```

**Example 3:**   
```
Input:
N = 3
arr[] = {1,2,3}
Output: -1 -1
Explanation: In the given array, there's no
repeating element, and thus the given Output.
```

### Constraints

+ `1 <= N <= 10^7`
+ `1 <= arrr[i] = 10^15`

## Solutions

```cpp
class Solution{
    public:
    //Function to find repeated element and its frequency.
    pair<int, int> findRepeating(int *arr, int n){
        int right = n-1, left = 0, freq = n - (arr[right] - arr[left]);
        while (left <= right) {
            int mid = (left+right)/2;
            if(arr[mid] == arr[mid+1] || arr[mid] == arr[mid-1])
                return {arr[mid], freq};
            else if (arr[mid]  - arr[left] == mid-left) {
                left = mid+1;
            } else {
                right = mid-1;
            }
        }
        return {-1, -1};
    }
};
```

