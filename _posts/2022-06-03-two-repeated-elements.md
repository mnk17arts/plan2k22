---
layout: post
title: Two Repeated Elements 
summary:
tags:
    - array
    - searching
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/two-repeated-elements-1587115621/1/#)  

You are given an array of `N+2` integer elements. All elements of the array are in range `1` to `N`. Also, all elements occur once except two numbers which occur twice. Find the two repeating numbers.

**Your Task:** 
The task is to complete the function `repeatedElements()` which takes array `arr[] `and an integer `N` as inputs (the size of the array is `N + 2` and elements are in `range[1, N]`) and finds the two repeated element in the array and return them in a list.
**Note:** Return the numbers in their order of appearing twice. So, if `X` and `Y` are the repeating numbers, and `X` repeats twice before `Y` repeating twice, then the order should be (`X,Y`).

**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
N = 4
array[] = {1,2,1,3,4,3}
Output: 1 3
Explanation: In the given array, 
1 and 3 are repeated two times.
```

**Example 2:**   
```
Input:
N = 2
array[] = {1,2,2,1}
Output: 2 1
Explanation: In the given array,
1 and 2 are repeated two times 
and second occurence of 2 comes 
before 1. So the output is 2 1.
```

### Constraints

+ `2 <= N <= 10^5`
+ `1 <= arrray[i] = N`

## Solutions

```cpp
class Solution{
    public:
    //Function to find two repeated elements.
    vector<int> twoRepeated (int arr[], int N) {
        // Your code here
        vector<int> res;
        for(int i = 0; i < N+2; i++) {
            int index = abs(arr[i]) - 1;
            if(arr[index] < 0) 
                res.push_back(abs(arr[i]));
            arr[index] = -arr[index];
        }
        return res;
    }
};
```

