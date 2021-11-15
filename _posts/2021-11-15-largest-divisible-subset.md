---
layout: post
title: Largest Divisible Subset
description: 
summary:
tags:
    - array
    - dynamic-programming
    - sorting
    - leetcode
    - cpp
    - medium
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/largest-divisible-subset)  

Given a set of distinct positive integers `nums`, return the largest subset answer such that every pair `(answer[i], answer[j])` of elements in this subset satisfies:

+ `answer[i] % answer[j] == 0`, or
+ `answer[j] % answer[i] == 0`
If there are multiple solutions, return any of them.

### Examples

**Example 1:**    
```
Input: nums = [1,2,3]
Output: [1,2]
Explanation: [1,3] is also accepted.
```

**Example 2:**    
```
Input: nums = [1,2,4,8]
Output: [1,2,4,8]
```

### Constraints
+ `1 <= nums.length <= 1000`
+ `1 <= nums[i] <= 2 * 10^9`
+ All the integers in `nums` are unique.

## Solutions

```cpp
class Solution {
public:
    vector<int> largestDivisibleSubset(vector<int>& nums) {
      int it{};
      int n = nums.size();
      vector<int> dp(n, 1);
      vector<int> id(n,-1);
      sort(nums.begin(), nums.end());
      for(int i{1}; i<n; i++){
        for(int j{i-1}; j>=0; j--){
          if(nums[i]%nums[j]==0){
            if(dp[j]+1 > dp[i]){
             dp[i] = dp[j]+1;
             id[i] = j;              
            }
          }
        }
        if(dp[i] > dp[it]) it = i;
      }
      vector<int> res;
      while(it!=-1){
        res.push_back(nums[it]);
        it = id[it];
      }
      
      return res;
    }
};
```

