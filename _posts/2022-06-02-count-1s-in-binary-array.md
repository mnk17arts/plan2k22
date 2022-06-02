---
layout: post
title: Count 1's in binary array
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

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/count-1s-in-binary-array-1587115620/1/)  

Given a binary sorted non-increasing array of 1s and 0s. You need to print the **count of 1s** in the binary array.

**Your Task:** 
The task is to complete the function `countOne()` which takes the array `arr[]` and its size `N` as inputs and returns the count of 1s in the input array.

**Expected Time Complexity:** `O(logN)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
N = 8
arr[] = {1,1,1,1,1,0,0,0}
Output: 5
Explanation: Number of 1's in given 
binary array : 1 1 1 1 1 0 0 0 is 5.
```

**Example 2:**   
```
Input:
N = 8
arr[] = {1,1,0,0,0,0,0,0}
Output: 2
Explanation: Number of 1's in given 
binary array : 1 1 0 0 0 0 0 0 is 2
```

### Constraints

+ `1 <= N <= 5*10^6`
+ `arr[i] = 0,1`

## Solutions

```cpp
class Solution{
    public:
    // Function to count number of Ones
    // arr: input array 
    // N: size of input array
    int countOnes(int arr[], int N)
    {        
        int left = 0, right = N-1;
        while(left <= right){
            int mid = left + (right-left)/2 ;
            if(arr[mid] == 1){
                if(mid == N-1 || arr[mid+1] == 0)
                    return mid+1;
                left = mid+1;
            }
            else 
                right = mid-1;
        }
        return 0;
            
    }
};
```

