---
layout: post
title: Two Out of Three
description: 
summary: 
tags:
    - array
    - leetcode
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/two-out-of-three/)
Given three integer arrays `nums1`, `nums2`, and `nums3`, return *a **distinct** array containing all the values that are present in** at least two** out of the three arrays. You may return the values in **any** order.*


### Examples
**Example 1:**  
```
Input: nums1 = [1,1,3,2], nums2 = [2,3], nums3 = [3]
Output: [3,2]
Explanation: The values that are present in at least two arrays are:
- 3, in all three arrays.
- 2, in nums1 and nums2.
```

**Example 2:**  
```
Input: nums1 = [3,1], nums2 = [2,3], nums3 = [1,2]
Output: [2,3,1]
Explanation: The values that are present in at least two arrays are:
- 2, in nums2 and nums3.
- 3, in nums1 and nums2.
- 1, in nums1 and nums3.
```

**Example 3:**  
```
Input: nums1 = [1,2,2], nums2 = [4,3,3], nums3 = [5]
Output: []
Explanation: No value is present in at least two arrays.
```

### Constraints
+ `1 <= nums1.length, nums2.length, nums3.length <= 100`
+ `1 <= nums1[i], nums2[j], nums3[k] <= 100`

## Solutions
```cpp
class Solution {
public:
    vector<int> twoOutOfThree(vector<int>& nums1, vector<int>& nums2, vector<int>& nums3) {
        vector<int> ans;
        set<int> one,two,three;
        for(int i=0; i<nums1.size();i++)
            one.insert(nums1[i]); 
        for(int i=0; i<nums2.size();i++)
            two.insert(nums2[i]);
        for(int i=0; i<nums3.size();i++)
            three.insert(nums3[i]);
        for( auto elem: one)
            if(two.find(elem)!=two.end() || three.find(elem)!=three.end())
                ans.push_back(elem);
        for( auto elem: two)
            if(three.find(elem)!=three.end() && one.find(elem)==one.end())
                ans.push_back(elem);  
        return ans;
    }
};
```
