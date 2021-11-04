---
layout: post
title: Number of Longest Increasing Subsequence
description: 
summary:
tags:
    - array
    - dynamic-programming
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/number-of-longest-increasing-subsequence/)
Given an integer array nums, return the number of longest increasing subsequences.

Notice that the sequence has to be strictly increasing.

### Examples

**Example 1:**  
```
Input: nums = [1,3,5,4,7]
Output: 2
Explanation: The two longest increasing subsequences are [1, 3, 4, 7] and [1, 3, 5, 7].
```

**Example 2:**  
```
Input: nums = [2,2,2,2,2]
Output: 5
Explanation: The length of longest continuous increasing subsequence is 1, and there are 5 subsequences' length is 1, so output 5.
```

### Constraints
+ `1 <= nums.length <= 2000`
+ `-10^6 <= nums[i] <= 10^6`

## Solutions

```cpp
class Solution {
public:
    int findNumberOfLIS(vector<int>& nums) {
      int n = nums.size();
      if(n==1) return 1;
      int L = INT_MIN; 
      int dp[n][2];
      dp[0][0] = dp[0][1] = 1;
      for(int i=1; i<n; i++){
        int l = INT_MIN;
        int w = 0; 
        for(int j=i-1; j>=0; j--)
          if(nums[j]<nums[i])
            l = max(l,dp[j][0]);
        for(int j=i-1; j>=0; j--)
          if(l==dp[j][0] and nums[j]<nums[i])
            w+= dp[j][1];
        if(l!=INT_MIN){
          dp[i][0] = l+1;
          dp[i][1] = w;
        }else{
          dp[i][0] = dp[i][1] = 1;
        }
        if(L < dp[i][0])
          L = dp[i][0];
      }
      
      int res = 0;
      for(int i=0; i<n; i++)
        if(L==dp[i][0])
          res+=dp[i][1];
      
      return res;
    }
};
```

