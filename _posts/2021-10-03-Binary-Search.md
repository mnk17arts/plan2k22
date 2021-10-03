---
layout: post
title: Binary Search
description: 
summary: 
tags:
    - binary-search
    - array
    - leetcode
    - cpp
    - easy
minute: 2 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/binary-search/)
Given an array of integers `nums` which is sorted in ascending order, and an integer `target`, write a function to search `target` in `nums`. If `target` exists, then return its index. Otherwise, return `-1`.

You must write an algorithm with `O(log n)` runtime complexity.

### Examples
**Example 1:**
```
Input: nums = [-1,0,3,5,9,12], target = 9
Output: 4
Explanation: 9 exists in nums and its index is 4
```

**Example 2:**
```
Input: nums = [-1,0,3,5,9,12], target = 2
Output: -1
Explanation: 2 does not exist in nums so return -1
```

### Constraints
+ `1 <= nums.length <= 10^4`
+ `-10^4 < nums[i], target < 10^4`
+ All the integers in `nums` are **unique**.
+ `nums` is sorted in ascending order.

## Solution
```cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int first = 0, last = nums.size()-1, mid;
        // Binary search algorithm
        while(first <= last){
            mid = first + (last-first)/2 ;
            if(nums[mid] == target){
                return mid ;
            }else if(nums[mid] > target){
                last = mid - 1 ;
            }else{
                first = mid + 1 ;
            }
        }
        return -1;
    }
};
```
