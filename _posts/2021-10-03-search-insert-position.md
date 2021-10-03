---
layout: post
title: Search Insert Position
description: 
summary: 
tags:
    - binary-search
    - array
    - leetcode
    - cpp
    - medium
minute: 5 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/search-insert-position/)
Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You must write an algorithm with `O(log n)` runtime complexity.

### Examples
**Example 1:**
```
Input: nums = [1,3,5,6], target = 5
Output: 2
```

**Example 2:**
```
Input: nums = [1,3,5,6], target = 2
Output: 1
```

**Example 3:**
```
Input: nums = [1,3,5,6], target = 7
Output: 4
```

**Example 4:**
```
Input: nums = [1,3,5,6], target = 0
Output: 0
```

**Example 5:**
```
Input: nums = [1], target = 0
Output: 0
```

### Constraints
+ `1 <= nums.length <= 10^4`
+ `-10^4 <= nums[i] <= 10^4`
+ nums contains **distinct** values sorted in **ascending** order.
+ `-10^4 <= target <= 10^4`

## Solution
```cpp
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        int first = 0, last = nums.size()-1, mid;
        // Binary search algorithm
        mid = first + (last-first)/2 ;
        while(first <= last){
            if(nums[mid] == target){
                return mid ;
            }else if(nums[mid] > target){
                last = mid - 1 ;
            }else{
                first = mid + 1 ;
            }
            mid = first + (last-first)/2 ;
        }
        return mid; 
    }
};
```
