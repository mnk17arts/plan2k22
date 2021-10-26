---
layout: post
title: Next Permutation
description: 
summary: 
tags:
    - array
    - pointers
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/next-permutation/)
Implement **next permutation**, which rearranges numbers into the lexicographically next greater permutation of numbers.

If such an arrangement is not possible, it must rearrange it as the lowest possible order (i.e., sorted in ascending order).

The replacement must be [in place](http://en.wikipedia.org/wiki/In-place_algorithm) and use only constant extra memory.

**Note**: The solution set must not contain duplicate combinations.
 
### Examples   
**Example 1:**  
```
Input: nums = [1,2,3]
Output: [1,3,2]
```

**Example 2:**  
```
Input: nums = [3,2,1]
Output: [1,2,3]
```

**Example 3:**  
```
Input: nums = [1,1,5]
Output: [1,5,1]
```

**Example 4:**  
```
Input: nums = [1]
Output: [1]
```

### Constraints
+ `1 <= nums.length <= 100`
+ `0 <= nums[i] <= 100`

## Solutions

```cpp
class Solution {
public:
    void nextPermutation(vector<int>& nums) {
        int r = nums.size()-2, l;
        while(r>=0  and nums[r] >= nums[r+1]) r--;
        if(r>=0){
            l = nums.size()-1;
            while(nums[l]<=nums[r]) l--;
            swap(nums[l],nums[r]);
        }
        reverse(nums.begin()+r+1,nums.end());

    }
};
```

