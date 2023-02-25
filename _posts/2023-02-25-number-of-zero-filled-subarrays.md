---
layout: post
title: Number of Zero-Filled Subarrays
summary:
tags:
  - leetcode
  - array
  - math
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/number-of-zero-filled-subarrays/)

Given an integer array nums, return the number of subarrays filled with 0.

A subarray is a contiguous non-empty sequence of elements within an array.

### Examples

**Example 1:**  
```
Input: nums = [1,3,0,0,2,0,0,4]
Output: 6
Explanation: 
There are 4 occurrences of [0] as a subarray.
There are 2 occurrences of [0,0] as a subarray.
There is no occurrence of a subarray with a size more than 2 filled with 0. Therefore, we return 6.
```

**Example 2:**  
```
Input: nums = [0,0,0,2,0,0]
Output: 9
Explanation:
There are 5 occurrences of [0] as a subarray.
There are 3 occurrences of [0,0] as a subarray.
There is 1 occurrence of [0,0,0] as a subarray.
There is no occurrence of a subarray with a size more than 3 filled with 0. Therefore, we return 9.
```

**Example 3:**  
```
Input: nums = [2,10,2019]
Output: 0
Explanation: There is no subarray filled with 0. Therefore, we return 0.
```

### Constraints

- `1 <= nums.length <= 10^5`
- `-10^9 <= nums[i] <= 10^9`

## Solutions

```cpp

class Solution {
public:
    long long zeroFilledSubarray(vector<int>& nums) {
        long long res = 0;
        long long cur = 0;
        for(int &i: nums) {
            if(i == 0) {
                cur++;
            }
            else {
                res += (cur * (cur + 1)) / 2;
                cur = 0;
            }
        }
        if(cur != 0) {
            res += (cur * (cur + 1)) / 2;
        }
        return res;
    }
};

```
