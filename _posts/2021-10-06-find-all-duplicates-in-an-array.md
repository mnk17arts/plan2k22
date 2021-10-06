---
layout: post
title: Find All Duplicates in an Array
description: 
summary: 
tags:
    - array
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/find-all-duplicates-in-an-array/)
Given an integer array `nums` of length `n` where all the integers of `nums` are in the range `[1, n]` and each integer appears **once or twice**, return *an array of all the integers that appears twice*.

You must write an algorithm that runs in `O(n)` time and uses only constant extra space.



### Examples
**Example 1:**
```
Input: nums = [4,3,2,7,8,2,3,1]
Output: [2,3]
```

**Example 2:**
```
Input: nums = [1,1,2]
Output: [1]
```

**Example 3:**
```
Input: nums = [1]
Output: []
```

### Constraints
+ `n == nums.length`
+ `1 <= n <= 10^5`
+ `1 <= nums[i] <= n`
+ Each element in nums appears **once or twice**

## Solutions
### 1
```cpp
class Solution {
public:
    vector<int> findDuplicates(vector<int>& nums) {
        vector<int> mnk;
        sort(nums.begin(),nums.end());
        for(int i = 0; i < nums.size()-1; i++){
            if(nums[i] == nums[i+1]){
                mnk.push_back(nums[i]);
            }
        }
        return mnk;
    }
};
```

### 2
```cpp
class Solution {
public:
    vector<int> findDuplicates(vector<int>& nums) {
        for(int num : nums)
        {
            int idx = abs(num) - 1;
            if(0 > nums[idx]) ans.push_back(idx+1);
            else    nums[idx] *= -1;
        }
        return ans;
    }
    private:
    vector<int> ans;
    
};
```
