---
layout: post
title:  Permutations II
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

## Problem Statement - [*link*](https://leetcode.com/problems/permutations-ii/)
Given a collection of numbers, `nums`, that might contain duplicates, return *all possible unique permutations in any order.*
 
### Examples   
**Example 1:**  
```
Input: nums = [1,1,2]
Output:
[[1,1,2],
 [1,2,1],
 [2,1,1]]
```

**Example 2:**  
```
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

### Constraints
+ `1 <= nums.length <= 8`
+ `-10 <= nums[i] <= 10`

## Solutions

```cpp
class Solution {
public:
    set<vector<int>> s;    
    void rc(vector<int>& nums, int i){
        if(i == nums.size()-1){
            s.insert(nums); 
            return ;
        }
        for(int j=i; j<nums.size(); j++){
            swap(nums[j],nums[i]);
            rc(nums,i+1);
            swap(nums[j],nums[i]);
        }
    }
    vector<vector<int>> permuteUnique(vector<int>& nums) {
        vector<vector<int>> res;
        rc(nums, 0);
        for(auto i: s) res.push_back(i);
        return res;
    }
};
```

