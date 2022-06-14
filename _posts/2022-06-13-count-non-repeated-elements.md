---
layout: post
title: Count Non-Repeated Elements 
summary:
tags:
    - hash
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/count-distinct-elements-1587115620/0/)  

Hashing is very useful to keep track of the frequency of the elements in a list.

You are given an array of integers. You need to print the count of non-repeated elements in the array.

**Your Task:** 
You don't need to read input or print anything. You only need to complete the function `countNonRepeated()` that takes array `arr[]` and its size `n` as parameters and returns the count of non-repeating elements in the array.


**Expected Time Complexity:** `O(n)`  
**Expected Auxiliary Space:** `O(n)`

### Examples

**Example 1:**   
```
Input:
10
1 1 2 2 3 3 4 5 6 7

Output: 
4

Explanation: 
4, 5, 6 and 7 are the 
elements with frequency 1 and rest 
elements are repeated so the number 
of non-repeated elements are 4.
```

**Example 2:**   
```
Input:
5
10 20 30 40 10

Output: 
3

Explanation: 
20, 30, 40 are the 
elements with the frequency 1 and 
10 is the repeated element to 
number of non-repeated elements 
are 3.
```

### Constraints

+ `1 <= N < 1000`
+ `0 <= arr[i] <= 10^7` 

## Solutions

```cpp
class Solution{
    public:
    //Complete this function
    //Function to return the count of non-repeated elements in the array.
    int countNonRepeated(int arr[], int n)
    {
        //Your code here
        int res = 0;
        unordered_map<int, int> m;
        for(int i=0; i<n; i++) m[arr[i]]++;
        for(auto i: m)
            if(i.second == 1) res++;
        return res;
    }
};
```

