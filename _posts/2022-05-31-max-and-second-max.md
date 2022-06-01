---
layout: post
title:  Max and Second Max 
summary:
tags:
    - array
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/max-and-second-max/1/)  

Given an array `arr[]` of size `N` of positive integers which may have duplicates. The task is to find the maximum and second maximum from the array, and both of them should be different from each other, so If no second max exists, then the second max will be `-1`.


**Your Task:** 
The task is to complete the function `largestAndSecondLargest()`, which should return maximum and second maximum element from the array with first element as maximum element and second element as second maximum(if there is no second maximum the  second element should be -1)

**Expected Time Complexity**: `O(N)`.     
**Expected Auxiliary Space**: `O(1)`.


### Examples

**Example 1:**   
```
Input:
N = 3
arr[] = {2,1,2}
Output: 2 1
Explanation: From the given array 
elements, 2 is the largest and 1 
is the second largest.
```

**Example 2:**   
```
Input:
N = 5
arr[] = {1,2,3,4,5}
Output: 5 4
Explanation: From the given array 
elements, 5 is the largest and 4 
is the second largest.
```

### Constraints

+ `1 <= N <= 10^6`
+ `1 <= arr[i] <= 10^6`

## Solutions

```cpp
class Solution
{
    public:
    /* Function to find largest and second largest element
    *sizeOfArray : number of elements in the array
    * arr = input array
    */
    vector<int> largestAndSecondLargest(int sizeOfArray, int arr[]){
        int max = INT_MIN, max2= INT_MIN;
        
        /*********************************
         * Your code here
         * This function should return a
         * vector with first element as
         * max and second element as 
         * second max
         * *******************************/
        for(int i=0; i<sizeOfArray; i++){
            if(max < arr[i]){
                max2 = max;
                max = arr[i];
            } 
            else if(max2 < arr[i] and max!=arr[i])
                max2 = arr[i];
        }
        if(max2 == INT_MIN) max2=-1;
        vector<int> res(2);
        res[0] = max;
        res[1] = max2;
        return res;
         
    }
};
```

