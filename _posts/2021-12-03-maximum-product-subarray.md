---
layout: post
title: Maximum Product Subarray
summary:
tags:
    - array
    - leetcode
    - cpp
    - medium
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/maximum-product-subarray)  

Given an integer array `nums`, find a contiguous non-empty subarray within the array that has the largest product, and return *the product.*

It is **guaranteed** that the answer will fit in a **32-bit** integer.

A **subarray** is a contiguous subsequence of the array.

### Examples

**Example 1:**   
```
Input: nums = [2,3,-2,4]
Output: 6
Explanation: [2,3] has the largest product 6.
```

**Example 2:**  
```
Input: nums = [-2,0,-1]
Output: 0
Explanation: The result cannot be 2, because [-2,-1] is not a subarray.
```

### Constraints
+ `1 <= nums.length <= 2 * 10^4`
+ `-10 <= nums[i] <= 10`
+ The product of any prefix or suffix of `nums` is **guaranteed** to fit in a **32-bit** integer.

## Solutions

```cpp
class Solution {
public:
    int maxProduct(vector<int>& nums) {
      int res = INT_MIN, l = 1, r = 1;
      int n = nums.size();
      for(int i = 0; i<n; i++){
        l = l*nums[i];
        r = r*nums[n-1-i];
        res = max(res, max(l, r));
        if(l==0) l=1;
        if(r==0) r=1;
      }
      return res; 
    }
};
```

