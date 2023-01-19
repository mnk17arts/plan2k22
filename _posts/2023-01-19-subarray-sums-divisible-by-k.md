---
layout: post
title: Subarray Sums Divisible by K                       
summary:
tags:
    - leetcode
    - array
    - hash
    - prefix-sum
    - cpp
    - medium
minute: 10+ min
---

## Problem Statement - [*link*](https://leetcode.com/problems/subarray-sums-divisible-by-k/description//)  

Given an integer array nums and an integer k, return the number of non-empty subarrays that have a sum divisible by k.

A subarray is a contiguous part of an array.

### Examples


**Example 1:**   
```
Input: nums = [4,5,0,-2,-3,1], k = 5
Output: 7
Explanation: There are 7 subarrays with a sum divisible by k = 5:
[4, 5, 0, -2, -3, 1], [5], [5, 0], [5, 0, -2, -3], [0], [0, -2, -3], [-2, -3]
```


**Example 2:**   
```
Input: nums = [5], k = 9
Output: 0

```


### Constraints

+ `1 <= nums.length <= 3 * 104`
+ `-10^4 <= nums[i] <= 10^4`
+ `2 <= k <= 10^4`

## Solutions

```cpp
class Solution {
public:
    int subarraysDivByK(vector<int>& nums, int k) {
        unordered_map<int,int> m;
        m[0]=1;
        int sum = 0, result = 0;
        for( int n: nums ) {
            sum = ( sum + n ) % k;
            if( sum < 0 ) {
                sum += k;
            }
            if( m.count(sum) ) {
                result += m[sum];
            } 
            m[sum]++;
        }
        return result;
    }
};
```

