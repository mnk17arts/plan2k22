---
layout: post
title: Zero Sum Subarrays  
summary:
tags:
    - hash
    - geeksforgeeks
    - cpp
    - medium
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/zero-sum-subarrays1825/0/)  

You are given an array `arr[]` of size `n`. Find the total count of sub-arrays having their sum equal to `0`.


**Your Task:** 
You don't need to read input or print anything. Complete the function `findSubarray()` that takes the array `arr` and its size `n` as input parameters and returns the total number of sub-arrays with `0` sum. 


**Expected Time Complexity:** `O(n)`  
**Expected Auxiliary Space:** `O(n)`

### Examples

**Example 1:**   
```
Input:
n = 6
arr[] = {0,0,5,5,0,0}
Output: 6
Explanation: The 6 subarrays are 
[0], [0], [0], [0], [0,0], and [0,0].
```

**Example 2:**   
```
Input:
n = 10
arr[] = {6,-1,-3,4,-2,2,4,6,-12,-7}
Output: 4
Explanation: The 4 subarrays are [-1 -3 4]
[-2 2], [2 4 6 -12], and [-1 -3 4 -2 2]
```

### Constraints

+ `1 <= n <= 10^7`
+ `-10^10 <= arr[i] <= 10^10`

## Solutions

```cpp
class Solution{
    public:
    //Function to count subarrays with sum equal to 0.
    ll findSubarray(vector<ll> arr, int n ) {
        //code here
        unordered_map<ll,ll> s;
        ll sum = 0, res = 0;
        for(int i=0; i<n; i++){
            sum += arr[i];
            if(sum == 0) res++;
            if(s.find(sum) != s.end())
                res += s[sum];
            s[sum]++;
        }
        return res;
    }
};
```

