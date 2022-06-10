---
layout: post
title: Count the number of possible triangles
summary:
tags:
    - array
    - sorting
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/count-possible-triangles-1587115620/0/#)  

Given an unsorted array `arr[] `of `n` positive integers. Find the number of triangles that can be formed with three different array elements as lengths of three sides of triangles.

**Your Task:** 
This is a function problem. You only need to complete the function `findNumberOfTriangles()` that takes `arr[]` and `n` as input parameters and returns the count of total possible triangles.

**Expected Time Complexity:** `O(n^2)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input: 
n = 3
arr[] = {3, 5, 4}
Output: 
1
Explanation: 
A triangle is possible 
with all the elements 5, 3 and 4.
```

**Example 2:**   
```
Input: 
n = 5
arr[] = {6, 4, 9, 7, 8}
Output: 
10
Explanation: 
There are 10 triangles
possible  with the given elements like
(6,4,9), (6,7,8),...
```

### Constraints

+ `3 <= n <= 10^3`
+ `1 <= arr[i] = 10^3` 

## Solutions

```cpp
class Solution{
    public:
    //Function to count the number of possible triangles.
    int helper(int arr[], int one, int two, int three){
        int count = 0;
        while(one < two){
            if( (arr[one] + arr[two]) > three ){
                count += two-one;
                two--;
            }else one++;
        }
        return count;
    }
    
    int findNumberOfTriangles(int arr[], int n){
            // code here
            sort(arr, arr+n);
            int res = 0;
            for(int i=n-1; i>=2; i--)
                res += helper(arr, 0, i-1, arr[i]);
            return res;
    }
};
```

