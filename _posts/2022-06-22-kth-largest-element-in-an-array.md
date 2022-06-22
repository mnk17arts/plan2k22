---
layout: post
title: Kth Largest Element in an Array   
summary:
tags:
    - array
    - sorting
    - leetcode
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/kth-largest-element-in-an-array/)  

Given an integer array `nums` and an integer `k`, return the `kth` largest element in the array.

Note that it is the `kth` largest element in the sorted order, not the `kth` distinct element.

### Examples

**Example 1:**   
```
Input: nums = [3,2,1,5,6,4], k = 2
Output: 5
```

**Example 2:**   
```
Input: nums = [3,2,3,1,2,4,5,5,6], k = 4
Output: 4
```

### Constraints

+ `1 <= k <= nums.length <= 10^4`
+ `-10^4 <= nums[i] <= 10^4`

## Solutions

```cpp
class Solution{
    public:
    int lomutoPartition(vector<int> &nums, int l, int r){
        int pivot = nums[r];
        int start = l;
        for(int i=l; i<r; i++)
            if(nums[i]<pivot) swap(nums[start++], nums[i]);
        swap(nums[r], nums[start]);
        return start;
    }
    int findKthLargest(vector<int>& nums, int k) {
        int l = 0, r = nums.size()-1, n=nums.size();
        k = n - k + 1;
        while(l<=r){
            int p = lomutoPartition(nums, l, r);
            if(p==k-1) return nums[p];
            else if(p > k-1) r = p - 1;
            else l = p + 1;
        }
        return -1;
    }
};
```

