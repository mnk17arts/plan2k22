---
layout: post
title: Minimum Size Subarray Sum
description: 
summary: 
tags:
    - array
    - slidingwindow
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/minimum-size-subarray-sum/)
Given an array of positive integers `nums` and a positive integer target, return the minimal length of a contiguous subarray `[numsl, numsl+1, ..., numsr-1, numsr]` of which the sum is greater than or equal to target. If there is no such subarray, return `0` instead.

### Examples

**Example 1:**  
```
Input: target = 7, nums = [2,3,1,2,4,3]
Output: 2
Explanation: The subarray [4,3] has the minimal length under the problem constraint.
```

**Example 2:**  
```
Input: target = 4, nums = [1,4,4]
Output: 1
```

**Example 3:**  
```
Input: target = 11, nums = [1,1,1,1,1,1,1,1]
Output: 0
```

### Constraints
+ `1 <= target <= 10^9`
+ `1 <= nums.length <= 10^5`
+ `1 <= nums[i] <= 10^5`


## Solutions

```cpp

class Solution {
public:
    int minSubArrayLen(int target, vector<int>& nums) {
        int l=0,s=0,len=nums.size()+1; 
        for(int i=0; i<nums.size(); i++){
            s += nums[i];
            while(s >= target){
                len = min(len, i-l+1);
                s -= nums[l++];
            }
        }
        return len > nums.size() ? 0 : len;
    }
};

```
