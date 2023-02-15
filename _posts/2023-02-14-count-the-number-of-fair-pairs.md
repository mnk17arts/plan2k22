---
layout: post
title: Count the Number of Fair Pairs 
summary:
tags:
    - leetcode
    - math
    - cpp
    - easy
minute: 5+ min
---

## Problem Statement - [*link*](https://leetcode.com/problems/count-the-number-of-fair-pairs/description/)  

Given a 0-indexed integer array nums of size n and two integers lower and upper, return the number of fair pairs.

A pair (i, j) is fair if:

+ 0 <= i < j < n, and
+ lower <= nums[i] + nums[j] <= upper

### Examples


**Example 1:**   
```
Input: nums = [0,1,7,4,4,5], lower = 3, upper = 6
Output: 6
Explanation: There are 6 fair pairs: (0,3), (0,4), (0,5), (1,3), (1,4), and (1,5).
```

**Example 2:**   
```
Input: nums = [1,7,9,2,5], lower = 11, upper = 11
Output: 1
Explanation: There is a single fair pair: (2,3).
```


### Constraints

+ `1 <= nums.length <= 10^5`
+ `-10^9 <= nums[i] <= 10^9`
+ `-10^9 <= lower <= upper <= 10^9`


## Solutions

```cpp

class Solution {
public:
    long long countLess(vector<int>& nums, int val) {
        long long res = 0;
        for (int i = 0, j = nums.size() - 1; i < j; ++i) {
            while(i < j && nums[i] + nums[j] > val)
                --j;
            res += j - i;
        }        
        return res;
    }
    long long countFairPairs(vector<int>& nums, int lower, int upper) {
        sort(nums.begin(), nums.end());
        return countLess(nums, upper) - countLess(nums, lower - 1);
    }
};

```

