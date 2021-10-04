---
layout: post
title: Squares of a Sorted Array
description: 
summary: 
tags:
    - array
    - sorting
    - leetcode
    - cpp
    - easy
minute: 2 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/squares-of-a-sorted-array/)
Given an integer array `nums` sorted in **non-decreasing** order, return *an array of **the squares of each number** sorted in non-decreasing order*.

### Examples
**Example 1:**
```
Input: nums = [-4,-1,0,3,10]
Output: [0,1,9,16,100]
Explanation: After squaring, the array becomes [16,1,0,9,100].
After sorting, it becomes [0,1,9,16,100].
```

**Example 2:**
```
Input: nums = [-7,-3,2,3,11]
Output: [4,9,9,49,121]
```

### Constraints
+ `1 <= nums.length <= 10^4`
+ `-10^4 <= nums[i] <= 10^4`
+ `nums` is sorted in **non-decreasing** order.

## Solution
```cpp
class Solution {
public:
    vector<int> sortedSquares(vector<int>& nums) {
        
    int f=0, l=nums.size()-1;
    int i=l;
    vector<int> mnk(l+1,0);
    while(f <= l){
        if(abs(nums[f]) < abs(nums[l])){
            mnk[i] = pow(nums[l],2);
            i--;
            l--;
        }else{
            mnk[i] = pow(nums[f],2);
            i--;
            f++;
        }
    }
        return mnk;
    }
};
```
