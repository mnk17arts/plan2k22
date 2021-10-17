---
layout: post
title:  Find First and Last Position of Element in Sorted Array
description: 
summary: 
tags:
    - array
    - binary-search
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)
Given an array of integers `nums` sorted in ascending order, find the starting and ending position of a given `target` value.

If `target` is not found in the array, return `[-1, -1]`.

You must write an algorithm with `O(log n)` runtime complexity.
 

### Examples

**Example 1:**   
```
Input: nums = [5,7,7,8,8,10], target = 8
Output: [3,4]
```

**Example 2:**  
```
Input: nums = [5,7,7,8,8,10], target = 6
Output: [-1,-1]
```

**Example 3:**  
```
Input: nums = [], target = 0
Output: [-1,-1]
```

### Constraints
+ `0 <= nums.length <= 10^5`
+ `-10^9 <= nums[i] <= 10^9`
+ `nums` is a non-decreasing array.
+ `-10^9 <= target <= 10^9`

## Solutions

```cpp

class Solution {
public:
    vector<int> searchRange(vector<int>& nums, int target) {

      if(nums.size()==0) return {-1,-1};
      
      vector<int> ans(2);
      
      int l=0,r=nums.size()-1;
      
      while(l<=r){
        int mid = l+(r-l)/2;
        if(nums[mid] >= target){
          ans[0] = mid;
           r = mid-1;
        }
        else l = mid+1;
      }   
      
      l=0,r=nums.size()-1;
      
      while(l<=r){
        int mid = l+(r-l)/2;
        if(nums[mid] <= target){
          ans[1] = mid;
          l = mid+1;
        }
        else r = mid-1;
      }  
        
      if(nums[ans[0]]==target and nums[ans[1]]==target)
        return ans;
      
      return {-1,-1};
    }
};

```

