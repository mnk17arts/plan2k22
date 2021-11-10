---
layout: post
title: 3Sum Closest
description: 
summary:
tags:
    - array
    - pointers
    - sorting
    - leetcode
    - cpp
    - medium
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/3sum-closest)  
Given an integer array `nums` of length `n` and an integer `target`, find three integers in `nums` such that the sum is closest to `target`.

Return *the sum of the three integers*.

You may assume that each input would have exactly one solution.

### Examples

**Example 1:**    
```
Input: nums = [-1,2,1,-4], target = 1
Output: 2
Explanation: The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).
```

**Example 2:**   
```
Input: nums = [0,0,0], target = 1
Output: 0

```

### Constraints
+ `3 <= nums.length <= 1000`
+ `-1000 <= nums[i] <= 1000`
+ `-10^4 <= target <= 10^4`

## Solutions

```cpp
class Solution {
public:
    int threeSumClosest(vector<int>& nums, int target) {
      
      sort(nums.begin(), nums.end());
      
      int res;
      int l, r;
      int x=INT_MAX;
      
      for(int i=0; i<nums.size()-2; i++){
        
        l = i+1;
        r = nums.size()-1;
        while(l<r){
            int s = nums[i]+nums[l]+nums[r];
            int d = abs(target-s);
            if(s>target) r--;
            else if(s<target) l++;
            else return target;        
            if(x > d){
              res = s;
              x = d;
            }            
        }
        
      }
      
      return res;
    }
};
```

