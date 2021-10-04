---
layout: post
title: Rotate Array
description: 
summary: 
tags:
    - array
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/rotate-array/)
Given an array, rotate the array to the right by `k` steps, where `k` is non-negative.

### Examples
**Example 1:**
```
Input: nums = [1,2,3,4,5,6,7], k = 3
Output: [5,6,7,1,2,3,4]
Explanation:
rotate 1 steps to the right: [7,1,2,3,4,5,6]
rotate 2 steps to the right: [6,7,1,2,3,4,5]
rotate 3 steps to the right: [5,6,7,1,2,3,4]
```

**Example 2:**
```
Input: nums = [-1,-100,3,99], k = 2
Output: [3,99,-1,-100]
Explanation: 
rotate 1 steps to the right: [99,-1,-100,3]
rotate 2 steps to the right: [3,99,-1,-100]
```

### Constraints
+ `1 <= nums.length <= 10^5`
+ `-2^31 <= nums[i] <= 2^31 - 1`
+ `0 <= k <= 10^5`

### Follow up:
+ Try to come up with as many solutions as you can. There are at least **three** different ways to solve this problem.
+ Could you do it in-place with `O(1)` extra space?

## Solution
```cpp
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        k = k%nums.size();
        reverse(nums.end()-k,nums.end());
        reverse(nums.begin(),nums.end()-k);
        reverse(nums.begin(),nums.end());
    }
};
```
