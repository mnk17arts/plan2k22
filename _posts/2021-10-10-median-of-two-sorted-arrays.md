---
layout: post
title: Median of Two Sorted Arrays
description: 
summary: 
tags:
    - array
    - leetcode
    - cpp
    - hard
minute: 6 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/median-of-two-sorted-arrays/)
Given two sorted arrays `nums1` and `nums`2 of size `m` and `n` respectively, return **the median** of the two sorted arrays.

The overall run time complexity should be `O(log (m+n))`.


### Examples
**Example 1:**  
```
Input: nums1 = [1,3], nums2 = [2]
Output: 2.00000
Explanation: merged array = [1,2,3] and median is 2.
```

**Example 2:**  
```
Input: nums1 = [1,2], nums2 = [3,4]
Output: 2.50000
Explanation: merged array = [1,2,3,4] and median is (2 + 3) / 2 = 2.5.
```

**Example 3:**  
```
Input: nums1 = [0,0], nums2 = [0,0]
Output: 0.00000
```

**Example 4:**  
```
Input: nums1 = [], nums2 = [1]
Output: 1.00000
```

### Constraints
+ `nums1.length == m`
+ `nums2.length == n`
+ `0 <= m <= 1000`
+ `0 <= n <= 1000`
+ `1 <= m + n <= 2000`
+ `-10^6 <= nums1[i], nums2[i] <= 10^6`

## Solutions
```cpp
class Solution {
public:
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        int a= nums1.size(), b = nums2.size();
        if( a == 0 &&b != 0){
            if( b%2 == 0){
                return double((nums2[b/2] + nums2[(b/2)-1]))/2 ;
            }else{
                return nums2[(b-1)/2];
            }
        }else if(a != 0 && b==0){
            if( a%2 == 0){
                return double((nums1[a/2] + nums1[(a/2)-1]))/2 ;
            }else{
                return nums1[(a-1)/2];
            }            
        }else
        {
            vector<int> arr ;
            int len = a + b ;
             while( a > 0 and b > 0 ){
                if(nums1[a-1] > nums2[b-1]){
                    arr.push_back(nums1[--a]);
                }else{
                    arr.push_back(nums2[--b]);
                }
            }
            
            if( a > 0){
                for(int i=a-1; i >= 0; i--){
                    arr.push_back(nums1[i]);
                }
            }
            if( b > 0){
                for(int i=b-1; i >= 0; i--){
                    arr.push_back(nums2[i]);
                }
            }
            if( len%2 == 0){
                return double((arr[len/2] + arr[(len/2)-1]))/2 ;
            }else{
                return arr[(len-1)/2];
            }
    }
    }
};
```
