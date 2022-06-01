---
layout: post
title: Longest Subarray Of Evens And Odds 
summary:
tags:
    - array
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/longest-subarray-of-evens-and-odds/1/)  

You are given an array of size `n`. Find the maximum possible length of a subarray such that its elements are arranged alternately either as even and odd or odd and even .

**Your Task:** 
You don't need to take any input. Just complete the function `maxEvenOdd()` that returns the maximum length.

**Expected Time Complexity**: `O(N)`.     
**Expected Auxiliary Space:**   `O(1)`.


### Examples

**Example 1:**   
```
Input:
n = 5
a[] = {10,12,14,7,8}
Output: 3
Explanation: The max length of subarray
is 3 and the subarray is {14 7 8}. Here 
the array starts as an even element and 
has odd and even elements alternately.
```

**Example 2:**   
```
Input:
n = 2
a[] = {4,6}
Output: 1
Explanation: The array contains {4 6}. 
So, we can only choose 1 element as 
that will be the max length subarray.
```

### Constraints

+ `1 <= N <= 10^6`
+ `1 <= A[i] <= 10^3`

## Solutions

```cpp
class Solution
{
    public:
    //Complete this function
    //Function to find the length of longest subarray of even and odd numbers.
    int maxEvenOdd(int arr[], int n) 
    { 
       //Your code here
       int cur = 1, res = 1;
       for(int i=1; i<n ; i++){
           if( ((arr[i-1]%2==0) and (arr[i]%2==1)) or 
               ((arr[i-1]%2==1) and (arr[i]%2==0)) ){
                   cur++;
                   res = max(res, cur);
               }
            else
                cur = 1;
       }
       
       return res;
    }
};
```

