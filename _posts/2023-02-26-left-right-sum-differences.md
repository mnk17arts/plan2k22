---
layout: post
title: Left and Right Sum Differences
summary:
tags:
  - leetcode
  - math
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/left-and-right-sum-differences/description/)

Given a 0-indexed integer array nums, find a 0-indexed integer array answer where:

+ answer.length == nums.length.
+ answer[i] = |leftSum[i] - rightSum[i]|.

Where:

+ leftSum[i] is the sum of elements to the left of the index i in the array nums. If there is no such element, leftSum[i] = 0.
+ rightSum[i] is the sum of elements to the right of the index i in the array nums. If there is no such element, rightSum[i] = 0.

Return the array answer.

### Examples

**Example 1:**  
```
Input: nums = [10,4,8,3]
Output: [15,1,11,22]
Explanation: The array leftSum is [0,10,14,22] and the array rightSum is [15,11,3,0].
The array answer is [|0 - 15|,|10 - 11|,|14 - 3|,|22 - 0|] = [15,1,11,22].
```

**Example 2:**  
```
Input: nums = [1]
Output: [0]
Explanation: The array leftSum is [0] and the array rightSum is [0].
The array answer is [|0 - 0|] = [0].
```


### Constraints

- `1 <= nums.length <= 1000`
- `1 <= nums[i] <= 10^5`

## Solutions

```cpp

class Solution {
public:
    vector<int> leftRigthDifference(vector<int>& nums) {
        int total_sum = accumulate(nums.begin(), nums.end(), 0);
        int cur_sum = 0;
        vector<int> res;
        for(int &i: nums) {
            total_sum -= i;
            res.push_back(abs(total_sum - cur_sum));
            cur_sum += i;
        }
        return res;
    }
}

```
