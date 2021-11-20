---
layout: post
title: Single Element in a Sorted Array
summary:
tags:
    - array
    - binary-search
    - leetcode
    - cpp
    - medium
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/single-element-in-a-sorted-array)  

You are given a sorted array consisting of only integers where every element appears exactly twice, except for one element which appears exactly once.

Return *the single element that appears only once.*

Your solution must run in `O(log n)` time and `O(1)` space.



### Examples

**Example 1:**   
```
Input: nums = [1,1,2,3,3,4,4,8,8]
Output: 2
```

**Example 2:**    
```
Input: nums = [3,3,7,7,10,11,11]
Output: 10
```

### Constraints
+ `1 <= nums.length <= 10^5`
+ `0 <= nums[i] <= 10^5`

## Solutions

```cpp
class Solution {
public:
    int singleNonDuplicate(vector<int>& nums) {
      if(nums.size()==1) return nums[0];
      int l = 0, r = nums.size()-1;
      while(l<=r){
        int m = l + (r-l)/2 ;
        if(nums[m] == nums[m^1]) l = m+1;
        else r = m-1;
      }
      
      return nums[l];
    }
};
```

