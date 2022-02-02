---
layout: post
title: Maximum Product of Three Numbers
summary:
tags:
    - array
    - leetcode
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/maximum-product-of-three-numbers)  

Given an integer array `nums`, *find three numbers whose product is maximum and return the maximum product.*

### Examples

**Example 1:**  
```
Input: nums = [1,2,3]
Output: 6.
```

**Example 2:**  
```
Input: nums = [1,2,3,4]
Output: 24
```

**Example 3:**  
```
Input: nums = [-1,-2,-3]
Output: -6
```

### Constraints

+ `3 <= nums.length <= 10^4`
+ `-1000 <= nums[i] <= 1000`

## Solutions

```cpp
class Solution {
public:
    int maximumProduct(vector<int>& nums) {
      sort(nums.begin(), nums.end());
      return max(nums[0]*nums[1]*nums[size(nums)-1], nums[size(nums)-1]*nums[size(nums)-2]*nums[size(nums)-3]);
    }
};
```

