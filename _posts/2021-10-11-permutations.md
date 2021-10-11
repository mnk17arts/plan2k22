---
layout: post
title: Permutations
description: 
summary: 
tags:
    - array
    - backtracking
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/permutations/)
Given an array `nums` of distinct integers, return *all the possible permutations. You can return the answer in any order.*

 

### Examples
**Example 1:**  
```
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

**Example 2:**  
```
Input: nums = [0,1]
Output: [[0,1],[1,0]]
```

**Example 3:**  
```
Input: nums = [1]
Output: [[1]]
```

### Constraints
+ `1 <= nums.length <= 6`
+ `-10 <= nums[i] <= 10`
+ All the integers of `nums` are unique.

## Solutions
```cpp

class Solution {
public:
    void bt(vector<vector<int>> &res,vector<int> &nums,int i){
        if(i == nums.size()-1){
            res.push_back(nums); 
            return;
        }
        for(int j=i; j<nums.size(); j++){
            swap(nums[j],nums[i]);
            bt(res,nums,i+1);
            swap(nums[j],nums[i]);
        }
        
    }
    vector<vector<int>> permute(vector<int>& nums) {
        vector<vector<int>> res;
        bt(res,nums,0);
        return res;
    }
};

```
