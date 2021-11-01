---
layout: post
title:  Longest Increasing Subsequence
description: 
summary: 
tags:
    - array
    - binary-search
    - dynamic-programming
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/longest-increasing-subsequence/)
Given an integer array `nums`, return *the length of the longest strictly increasing subsequence.*

A **subsequence** is a sequence that can be derived from an array by deleting some or no elements without changing the order of the remaining elements. For example, `[3,6,2,7]` is a subsequence of the array `[0,3,1,6,2,2,7]`.

### Examples

**Example 1:**  
```
Input: nums = [10,9,2,5,3,7,101,18]
Output: 4
Explanation: The longest increasing subsequence is [2,3,7,101], therefore the length is 4.
```

**Example 2:**  
```
Input: nums = [0,1,0,3,2,3]
Output: 4
```

**Example 3:**  
```
Input: nums = [7,7,7,7,7,7,7]
Output: 1
```

### Constraints
+ `1 <= nums.length <= 2500`
+ `-10^4 <= nums[i] <= 10^4`

**Follow up:** Can you come up with an algorithm that runs in **`O(n log(n))`** time complexity?

## Solutions

```cpp
class Solution {
public:
    int lengthOfLIS(vector<int>& nums) {
      
      int n = nums.size();
      vector<int> v;
      v.push_back(nums[0]);
      
      for(int i=1; i<n; i++){
        
        if(nums[i] > v[v.size()-1])
          v.push_back(nums[i]);
        
        else{
          int l = 0, r = v.size()-1;
          
          while(l<r){
            
            int m = l+(r-l)/2 ;
            
            if(v[m] < nums[i]) l = m+1;
            
            else if(v[m] >= nums[i])
              r = m;
            
          }
          
          v[l] = nums[i];
        }
        
      }
      
      return v.size();
    }
};
```

