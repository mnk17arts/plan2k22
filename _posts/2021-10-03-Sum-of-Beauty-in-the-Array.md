---
layout: post
title: Sum of Beauty in the Array
description: 
summary: 
tags:
    - array
    - leetcode
    - cpp
    - medium
minute: 1
---

## Problem Statement - [*link*](https://leetcode.com/problems/sum-of-beauty-in-the-array/)
You are given a **0-indexed** integer array `nums`. For each index `i (1 <= i <= nums.length - 2)` the **beauty** of `nums[i]` equals:

+ `2`, if `nums[j] < nums[i] < nums[k]`, for **all** `0 <= j < i` and for **all** `i < k <= nums.length - 1`.
+ `1`, if `nums[i - 1] < nums[i] < nums[i + 1]`, and the previous condition is not satisfied.
+ `0`, if none of the previous conditions holds.

Return *the **sum of beauty** of all* `nums[i]` *where* `1 <= i <= nums.length - 2`.

### Examples
**Example 1:**
```
Input: nums = [1,2,3]
Output: 2
Explanation: For each index i in the range 1 <= i <= 1:
- The beauty of nums[1] equals 2
```

**Example 2:**
```
Input: nums = [2,4,6,4]
Output: 1
Explanation: For each index i in the range 1 <= i <= 2:
- The beauty of nums[1] equals 1.
- The beauty of nums[2] equals 0.
```

**Example 3:**
```
Input: nums = [3,2,1]
Output: 0
Explanation: For each index i in the range 1 <= i <= 1:
- The beauty of nums[1] equals 0.
```
### Constraints
+ `3 <= nums.length <= 10^5`
+ `1 <= nums[i] <= 10^5`

## Solution
```cpp
class Solution {
public:
    int sumOfBeauties(vector<int>& nums) {
        int summ = 0;
        vector<bool> flags ;
        flags.push_back(true);
        int mx = nums[0], mn = nums[nums.size()-1];
        
        for(int i=1; i < nums.size()-1 ; i++){
            mx = max(mx,nums[i-1]);
            if(nums[i] > mx){
                flags.push_back(true);
            }else{
                flags.push_back(false);
            }
        }
        
        for(int i=nums.size()-2; i >0  ; i--){
    
            mn = min(mn,nums[i+1]);
            if(nums[i] < mn){
                flags[i] = (flags[i] && true);
            }else{
                flags[i] = false;
            }
            
            if(flags[i]){
                summ+=2;
            }else if(nums[i-1]<nums[i] && nums[i]<nums[i+1]){
                summ+=1;
            }
        }
        return summ;
    }
};
```
