---
layout: post
title:  Subsets II
description: 
summary: 
tags:
    - array
    - bitmasks
    - backtracking
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/subsets-ii/)
Given an integer array `nums` that may contain duplicates, return *all possible subsets (the power set).*

The solution set **must not** contain duplicate subsets. Return *the solution in **any order**.*
 
### Examples   
**Example 1:**  
```
Input: nums = [1,2,2]
Output: [[],[1],[1,2],[1,2,2],[2],[2,2]]
```

**Example 2:**  
```
Input: nums = [0]
Output: [[],[0]]
```

### Constraints
+ `1 <= nums.length <= 10`
+ `-10 <= nums[i] <= 10`


## Solutions

```cpp
class Solution {
public:
    vector<vector<int>> subsetsWithDup(vector<int>& nums) {
        vector<vector<int>> res;
        set<vector<int>> s; 
        for(int i=0; i<pow(2,nums.size()); i++){
            vector<int> ss;
            for(int j=0; j<nums.size(); j++)
                if(i&(1<<j)) ss.push_back(nums[j]);
            sort(ss.begin(),ss.end());
            s.insert(ss);
        }
        for(auto i: s) res.push_back(i);
        return res;
    }
};
```

