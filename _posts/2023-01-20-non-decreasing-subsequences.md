---
layout: post
title: Non-decreasing Subsequences                       
summary:
tags:
    - leetcode
    - array
    - backtracking
    - hash
    - cpp
    - medium
minute: 10+ min
---

## Problem Statement - [*link*](https://leetcode.com/problems/non-decreasing-subsequences/description/)  

Given an integer array nums, return all the different possible non-decreasing subsequences of the given array with at least two elements. You may return the answer in any order.

### Examples


**Example 1:**   
```
Input: nums = [4,6,7,7]
Output: [[4,6],[4,6,7],[4,6,7,7],[4,7],[4,7,7],[6,7],[6,7,7],[7,7]]
```


**Example 2:**   
```
Input: nums = [4,4,3,2,1]
Output: [[4,4]]
```


### Constraints

+ `1 <= nums.length <= 15`
+ `-100 <= nums[i] <= 100`

## Solutions

```cpp

class Solution {
public:
    vector<int> temp;
    set<vector<int>> res;
    void helper(vector<int> &nums, int id) {
        int n = nums.size();
        if(id>=n) {
            if(temp.size()>=2) {
                res.insert(temp);
                // for(int i: temp)
                //     cout << i <<",";
                // cout<<endl;
            }
            return;
        }
        if( temp.empty() || (nums.at(id)>=temp.back()) ) {
            temp.push_back(nums.at(id));
            helper(nums, id+1);
            temp.pop_back();
        }
        helper(nums, id+1);
    }
    vector<vector<int>> findSubsequences(vector<int>& nums) {
        helper(nums, 0);
        return vector(res.begin(),res.end());
    }
};

```

