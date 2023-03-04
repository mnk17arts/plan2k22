---
layout: post
title: Count Subarrays With Fixed Bounds
summary:
tags:
  - leetcode
  - array
  - 2pointers
  - cpp
  - hard
minute: 10+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/count-subarrays-with-fixed-bounds/description/)

You are given an integer array nums and two integers minK and maxK.

A fixed-bound subarray of nums is a subarray that satisfies the following conditions:

+ The minimum value in the subarray is equal to minK.
+ The maximum value in the subarray is equal to maxK.

Return the number of fixed-bound subarrays.

A subarray is a contiguous part of an array.


### Examples

**Example 1:**  


```
Input: nums = [1,3,5,2,7,5], minK = 1, maxK = 5
Output: 2
Explanation: The fixed-bound subarrays are [1,3,5] and [1,3,5,2].
```

**Example 2:**  


```
Input: nums = [1,1,1,1], minK = 1, maxK = 1
Output: 10
Explanation: Every subarray of nums is a fixed-bound subarray. There are 10 possible subarrays.
```


### Constraints

- `2 <= nums.length <= 10^5`
- `1 <= nums[i], minK, maxK <= * 10^4`


## Solutions

```cpp

class Solution {
public:
    long long countSubarrays(vector<int>& nums, int minK, int maxK) {
        long long res = 0;
        int n = nums.size();
        int minI = -1, maxI = -1, startI = -1;
        for(int i = 0; i < n; i++) {
            if(minK <= nums[i] && nums[i] <= maxK) {
                minI = (nums[i] == minK) ? i : minI;
                maxI = (nums[i] == maxK) ? i : maxI;
                res += max(0, min(minI, maxI) - startI);
            }
            else {
                minI = -1, maxI = -1, startI = i;
            }
        }
        return res;
    }
};

```
