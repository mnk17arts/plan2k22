---
layout: post
title: Find All Numbers Disappeared in an Array
summary:
tags:
    - array
    - leetcode
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array)  

Given an array `nums` of `n` integers where `nums[i]` is in the range `[1, n]`, return *an array of all the integers in the range `[1, n]` that do not appear in `nums`*.

### Examples

**Example 1:**   
```
Input: nums = [4,3,2,7,8,2,3,1]
Output: [5,6]
```

**Example 2:**    
```
Input: nums = [1,1]
Output: [2]
```

### Constraints
+ `n == nums.length`
+ `1 <= n <= 10^5`
+ `1 <= nums[i] <= n`

## Solutions

```cpp
class Solution {
public:
    vector<int> findDisappearedNumbers(vector<int>& nums) {
      sort(nums.begin(), nums.end());
      vector<int> res;
      int k=1;
      for(int i=0; i<nums.size(); i++){
        
        if(k==nums[i]) k++;
        else if(k<nums[i]) {
          while(k<nums[i]){
             res.push_back(k);
             k++;
          }
          k++;
        }
        
      }
      
      while(k<=nums.size()) {
             res.push_back(k);
             k++;
          }
      return res;
    }
};
```

