---
layout: post
title: Single Number II
description: 
summary:
tags:
    - array
    - leetcode
    - cpp
    - easy
minute: 2 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/single-number-ii)  
Given an integer array `nums` where every element appears **three times** except for one, which appears **exactly once**. Find the single element and return it.

You must implement a solution with a linear runtime complexity and use only constant extra space.

### Examples

**Example 1:**    
```
Input: nums = [2,2,3,2]
Output: 3
```

**Example 2:**   
```
Input: nums = [0,1,0,1,0,1,99]
Output: 99
```

### Constraints
+ `1 <= nums.length <= 3 * 10^4`
+ `-2^31 <= nums[i] <= 2^31 - 1`
+ Each element in nums appears exactly three times except for one element which appears once.

## Solutions

```cpp
class Solution {
public:
    int singleNumber(vector<int>& nums) {
      sort(nums.begin(), nums.end());
      int c = 1, n=nums[0];
      for(auto i: nums) cout<<i<<" ";
      for(int i=1; i<nums.size(); i++){
        if(n==nums[i]) c++;
        else if(c==1) return n;
        else { c = 1; n = nums[i]; }
      }
      return n;
    }
};
```

