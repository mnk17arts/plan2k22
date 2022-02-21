---
layout: post
title: Majority Element
summary:
tags:
    - leetcode
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/majority-element)  

Given an array `nums` of size `n`, return *the majority element.*

The majority element is the element that appears more than `⌊n / 2⌋` times. You may assume that the majority element always exists in the array.

### Examples

**Example 1:**  
```
Input: nums = [3,2,3]
Output: 3
```

**Example 2:**  
```
Input: nums = [2,2,1,1,1,2,2]
Output: 2
```

### Constraints

+ `n == nums.length`
+ `1 <= n <= 5 * 10^4`
+ `-2^31 <= nums[i] <= 2^31 - 1`

## Solutions

```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
      sort(nums.begin(),nums.end());
      return nums[size(nums)/2]; 
    }
};
```