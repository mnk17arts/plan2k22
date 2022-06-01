---
layout: post
title: Leaders in an array  
summary:
tags:
    - array
    - geeksforgeeks
    - cpp
    - easy
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/leaders-in-an-array-1587115620/1/)  

Given an array `A` of positive integers. Your task is to find the leaders in the array. An element of array is leader if it is greater than or equal to all the elements to its right side. The rightmost element is always a leader. 




**Your Task:** 
You don't need to read input or print anything. The task is to complete the function `leader()` which takes array A and n as input parameters and returns an array of leaders in order of their appearance.

**Expected Time Complexity:** `O(n)`  
**Expected Auxiliary Space:** `O(n)`

### Examples

**Example 1:**   
```
Input:
n = 6
A[] = {16,17,4,3,5,2}
Output: 17 5 2
Explanation: The first leader is 17 
as it is greater than all the elements
to its right.  Similarly, the next 
leader is 5. The right most element 
is always a leader so it is also 
included.
```

**Example 2:**   
```
Input:
n = 5
A[] = {1,2,3,4,0}
Output: 4 0
```

### Constraints

+ `1 <= n <= 10^7`
+ `0 ≤ A[i] <= 10^7`

## Solutions

```cpp
class Solution{
    //Function to find the leaders in the array.
    public:
    vector<int> leaders(int a[], int n){
        // Code here
        vector<int> res;
        int m = a[n-1];
        res.push_back(m);
        for(int i=n-2; i>=0; i--){
            if(a[i] >= m){
                m = a[i];
                res.push_back(m);
            }
        }
        reverse(res.begin(), res.end());
        return res;        
    }
};
```

