---
layout: post
title: Two Sum II - Input array is sorted
description: 
summary: 
tags:
    - array
    - binary-search
    - leetcode
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)
Given a **1-indexed** array of integers `numbers` that is already ***sorted in non-decreasing*** order, find two numbers such that they add up to a specific `target` number. Let these two numbers be `numbers[index1]` and `numbers[index2]` where `1 <= first < second <= numbers.length`.

Return *the indices of the two numbers, `index1` and `index2`, as an integer array `[index1, index2]` of length 2*.

The tests are generated such that there is **exactly one solution**. You **may not** use the same element twice.



### Examples
**Example 1:**
```
Input: numbers = [2,7,11,15], target = 9
Output: [1,2]
Explanation: The sum of 2 and 7 is 9. Therefore index1 = 1, index2 = 2.
```

**Example 2:**
```
Input: numbers = [2,3,4], target = 6
Output: [1,3]
Explanation: The sum of 2 and 4 is 6. Therefore index1 = 1, index2 = 3.
```

**Example 3:**
```
Input: numbers = [-1,0], target = -1
Output: [1,2]
Explanation: The sum of -1 and 0 is -1. Therefore index1 = 1, index2 = 2.
```

### Constraints
+ `2 <= numbers.length <= 3 * 10^4`
+ `-1000 <= numbers[i] <= 1000`
+ `numbers` is sorted in **non-decreasing order**
+ `-1000 <= target <= 1000`
+ The tests are generated such that there is **exactly one solution**

## Solution
```cpp
class Solution {
public:
    int find2ndIndex(vector<int>& numbers,int left,int right,int t){
        while(left<=right){
            int mid = left + (right-left)/2;
            if(numbers[mid] == t){
                return mid;
            }else if(numbers[mid] > t){
                right = mid-1;
            }else{
                left = mid+1;
            }
        }
        return 0;
    }
    vector<int> twoSum(vector<int>& numbers, int target) {     
        for(int i=0; i<numbers.size();i++){
            int t = target - numbers[i];
            int left=i+1,right=numbers.size()-1,mid; 
            mid = find2ndIndex(numbers,left,right,t);
            if(mid)
                return {i+1,mid+1};
        }
        return {0,0};
    }
};
```
