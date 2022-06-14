---
layout: post
title: Subarray range with given sum  
summary:
tags:
    - hash
    - geeksforgeeks
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/subarray-range-with-given-sum0128/0/#)  

Given an unsorted array of integers and a sum. The task is to count the number of subarray which adds to the given sum.

**Your Task:** 
This is a function problem. You only need to complete the function `subArraySum()` that takes `arr`, `n`, `sum` as parameters and returns the count of subarrays which adds up to the given `sum`. 


**Expected Time Complexity:** `O(n)`  
**Expected Auxiliary Space:** `O(n)`

### Examples

**Example 1:**   
```
Input:
n = 5
arr[] = {10,2,-2,-20,10}
sum = -10
Output: 3
Explanation: Subarrays with sum -10 are: 
[10, 2, -2, -20], [2, -2, -20, 10] and 
[-20, 10].
```

**Example 2:**   
```
Input:
n = 6
arr[] = {1,4,20,3,10,5}
sum = 33
Output: 1
Explanation: Subarray with sum 33 is: 
[20,3,10].
```

### Constraints

+ `1 <= n <= 10^5`
+ `-10^5 <= arr[i] <= 10^5`
+ `-10^5 <= sum <= 10^5`

## Solutions

```cpp
class Solution{
    public:
    //Function to count the number of subarrays which adds to the given sum.
    int subArraySum(int arr[], int n, int sum)
    {
        //Your code here
        int res = 0, csum = 0;
        unordered_map<int, int> s;
        for(int i=0; i<n; i++){
            csum += arr[i];
            if(csum == sum) res++;
            if(s.find(csum-sum) != s.end())
                res += s[csum-sum];
            s[csum]++;
        }
        return res;
    }
};
```

