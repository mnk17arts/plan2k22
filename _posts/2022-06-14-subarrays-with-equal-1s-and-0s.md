---
layout: post
title: Subarrays with equal 1s and 0s  
summary:
tags:
    - hash
    - array
    - geeksforgeeks
    - cpp
    - medium
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/zero-sum-subarrays1825/0/)  

Given an array containing `0s` and `1s`. Find the number of subarrays having equal number of `0s` and `1s`.


**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `countSubarrWithEqualZeroAndOne()` which takes the array `arr[]` and the size of the array as inputs and returns the number of subarrays with equal number of `0s` and `1s`.


**Expected Time Complexity:** `O(n)`  
**Expected Auxiliary Space:** `O(n)`

### Examples

**Example 1:**   
```
Input:
n = 7
A[] = {1,0,0,1,0,1,1}
Output: 8
Explanation: The index range for the 8 
sub-arrays are: (0, 1), (2, 3), (0, 3), (3, 4), 
(4, 5) ,(2, 5), (0, 5), (1, 6)
```

**Example 2:**   
```
Input:
n = 5
A[] = {1,1,1,1,0}
Output: 1
Explanation: The index range for the 
subarray is (3,4).
```

### Constraints

+ `1 <= n <= 10^6`
+ `0 <= A[i] <= 1`

## Solutions

```cpp
class Solution{
    public:
    //Function to count subarrays with 1s and 0s.
    long long int countSubarrWithEqualZeroAndOne(int arr[], int n)
    {
        //Your code here
        unordered_map<int, long long> m;
        long long res = 0;
        int sum = 0;
        for(int i=0; i<n; i++){
            if(arr[i] == 0) arr[i] = -1;
            sum += arr[i];
            if(sum == 0) res++;
            if(m.find(sum) != m.end())
                res += m[sum];
            m[sum]++;
        }
        return res;
    }
};
```

