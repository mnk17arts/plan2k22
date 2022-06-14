---
layout: post
title: Subarray with 0 sum
summary:
tags:
    - hash
    - array
    - math
    - slidingwindow
    - geeksforgeeks
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/subarray-with-0-sum-1587115621/0)  

Given an array of positive and negative numbers. Find if there is a subarray (of size at-least one) with `0` sum.

**Your Task:** 
You only need to complete the function `subArrayExists()` that takes `array` and `n` as parameters and returns `true` or `false` depending upon whether there is a subarray present with `0`-sum or not. Printing will be taken care by the drivers code.


**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input:
5
4 2 -3 1 6

Output: 
Yes

Explanation: 
2, -3, 1 is the subarray 
with sum 0.
```

**Example 2:**   
```
Input:
5
4 2 0 1 6

Output: 
Yes

Explanation: 
0 is one of the element 
in the array so there exist a 
subarray with sum 0.
```

### Constraints

+ `1 <= N <= 10^4`
+ `-10^5 <= A[i] <= 10^5` 

## Solutions

```cpp
class Solution{
    public:
    //Complete this function
    //Function to check whether there is a subarray present with 0-sum or not.
    bool subArrayExists(int arr[], int n)
    {
        //Your code here
        unordered_set<int> s;
        int sum = 0;
        for(int i=0; i<n; i++){
            sum += arr[i];
            if(sum == 0) return true;
            if(s.find(sum) != s.end()) return true;
            s.insert(sum);
        }
        return false;
    }
};
```

