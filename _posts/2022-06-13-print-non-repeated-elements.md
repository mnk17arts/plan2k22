---
layout: post
title: Print Non-Repeated Elements
summary:
tags:
    - hash
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/print-distinct-elements-1587115620/0/)  

Hashing is very useful to keep track of the frequency of the elements in a list.

You are given an array of integers. You need to print the non-repeated elements as they appear in the array.

**Your Task:** 
You don't need to read input or print anything. You only need to complete the function `printNonRepeated()` that takes `arr` and `n` as parameters and return the array which has the distinct elements in **same order** as they appear in input array. The newline is appended automatically by the driver code. 


**Expected Time Complexity:** `O(n)`  
**Expected Auxiliary Space:** `O(n)`

### Examples

**Example 1:**   
```
Input:
n = 10
arr[] = {1,1,2,2,3,3,4,5,6,7}
Output: 4 5 6 7
Explanation: 4, 5, 6 and 7 are the only 
elements which is having only 1 
frequency and hence, Non-repeating.
```

**Example 2:**   
```
Input:
n = 5
arr[] = {10,20,40,30,10}
Output: 20 40 30
Explanation: 20, 40, 30 are the only 
elements which is having only 1 
frequency and hence, Non-repeating.
```

### Constraints

+ `1 <= N < 1000`
+ `0 <= arr[i] <= 10^7` 

## Solutions

```cpp
class Solution{
    public:
    // arr[]: input array
    // n: size of array
    //Function to return non-repeated elements in the array.
    vector<int> printNonRepeated(int arr[],int n)
    {
        //Your code here
        map<int, int> m;
        vector<int> res;
        for(int i=0; i<n; i++) m[arr[i]]++;
        for(int i=0; i<n; i++)
            if(m[arr[i]]==1)
                res.push_back(arr[i]);
        return res;
    }
};
```

