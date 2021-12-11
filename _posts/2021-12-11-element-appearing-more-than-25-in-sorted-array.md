---
layout: post
title: Element Appearing More Than 25% In Sorted Array
summary:
tags:
    - array
    - leetcode
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/element-appearing-more-than-25-in-sorted-array)  

Given an integer array **sorted** in non-decreasing order, there is exactly one integer in the array that occurs more than 25% of the time, return that integer.

### Examples

**Example 1:**  
```
Input: arr = [1,2,2,6,6,6,6,7,10]
Output: 6
```

**Example 2:**  
```
Input: arr = [1,1]
Output: 1
```

### Constraints
+ `1 <= arr.length <= 10^4`
+ `0 <= arr[i] <= 10^5`

## Solutions

```cpp
class Solution {
public:
    int findSpecialInteger(vector<int>& arr) {
      int c = 1, x = arr[0], k = arr.size() / 4;
      for(int i=1; i<arr.size(); i++){
        if(c>k) return arr[i-1];
        if(arr[i-1]==arr[i]) c++;
        else c=1, x = arr[i];
      }
      return x;
    }
};
```

