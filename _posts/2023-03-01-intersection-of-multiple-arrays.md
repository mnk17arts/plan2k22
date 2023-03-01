---
layout: post
title: Intersection of Multiple Arrays
summary:
tags:
  - leetcode
  - hash
  - array
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/intersection-of-multiple-arrays/description/)

Given a 2D integer array nums where nums[i] is a non-empty array of distinct positive integers, return the list of integers that are present in each array of nums sorted in ascending order.


### Examples

**Example 1:**  


```
Input: nums = [[3,1,2,4,5],[1,2,3,4],[3,4,5,6]]
Output: [3,4]
Explanation: 
The only integers present in each of nums[0] = [3,1,2,4,5], nums[1] = [1,2,3,4], and nums[2] = [3,4,5,6] are 3 and 4, so we return [3,4].
```

**Example 2:**  


```
Input: nums = [[1,2,3],[4,5,6]]
Output: []
Explanation: 
There does not exist any integer present both in nums[0] and nums[1], so we return an empty list [].
```


### Constraints

- `1 <= nums.length <= 1000`
- `1 <= sum(nums[i].length) <= 1000`
- `1 <= nums[i][j] <= 1000`
- `nums[i]` is a non-empty array of distinct positive integers.

## Solutions

```cpp

class Solution {
public:
    vector<int> intersection(vector<vector<int>>& nums) {
        unordered_map<int, int> map;
        for(const auto &arr: nums) {
            for(const auto &num: arr) {
                map[num]++;
            }
        }
        int n = nums.size();
        vector<int> res;
        for(const auto &it: map) {
            if(it.second == n) {
                res.push_back(it.first);
            }
        }
        sort(res.begin(), res.end());
        return res;
    }
};

```
