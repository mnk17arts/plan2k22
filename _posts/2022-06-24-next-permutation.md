---
layout: post
title: Next Permutation   
summary:
tags:
    - string
    - dynamic-programming
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/next-permutation5226/1#)  

Implement the next permutation, which rearranges the list of numbers into Lexicographically next greater permutation of list of numbers. If such arrangement is not possible, it must be rearranged to the lowest possible order i.e. sorted in an ascending order. You are given an list of numbers `arr[ ]` of size `N`.

**Your Task:** 
You do not need to read input or print anything. Your task is to complete the function `nextPermutation()` which takes `N` and `arr[ ]` as input parameters and returns a list of numbers containing the next permutation.



**Expected Time Complexity:** `O(N)` 
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input: N = 6
arr = {1, 2, 3, 6, 5, 4}
Output: {1, 2, 4, 3, 5, 6}
Explaination: The next permutation of the 
given array is {1, 2, 4, 3, 5, 6}.
```

**Example 2:**   
```
Input: N = 3
arr = {3, 2, 1}
Output: {1, 2, 3}
Explaination: As arr[] is the last 
permutation. So, the next permutation 
is the lowest one.
```

### Constraints

+ `1 <= N <= 10000`

## Solutions

```cpp
class Solution{
    public:
    vector<int> nextPermutation(int N, vector<int> arr){
        // code here
        int i=N-1;
        while(arr[i-1]>=arr[i]&&i>=1) i--;
        if(i==0) reverse(arr.begin(),arr.end());
        else{
            reverse(arr.begin()+i,arr.end());
            int k=i-1;
            while(arr[k]>=arr[i]) i++;
            swap(arr[k],arr[i]);
        }        
        return arr;    
    }
};
```

