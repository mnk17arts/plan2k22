---
layout: post
title: Partition Equal Subset Sum
description: 
summary: 
tags:
    - array
    - bitset
    - dynamic-programming
    - leetcode
    - cpp
    - medium
minute: 6 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/partition-equal-subset-sum/)


Given a non-empty array `nums` containing only positive integers, find if the array can be partitioned into two subsets such that the sum of elements in both subsets is equal.



### Examples
**Example 1:**
```
Input: nums = [1,5,11,5]
Output: true
Explanation: The array can be partitioned as [1, 5, 5] and [11].
```

**Example 2:**
```
Input: nums = [1,2,3,5]
Output: false
Explanation: The array cannot be partitioned into equal sum subsets.
```


### Constraints
+ `1 <= nums.length <= 200`
+ `1 <= nums[i] <= 100`


## Solution
```cpp
class Solution {
public:
    bool canPartition(vector<int>& a) {
        int sum = accumulate(nums.begin(), nums.end(), 0); 
        if (sum%2) return false; 
        bitset<20001> bits(1); 
        for (auto &num : nums) bits |= bits << num; 
        return bits[sum/2]; 
    }
};
```
