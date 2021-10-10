---
layout: post
title: Bitwise AND of Numbers Range
description: 
summary: 
tags:
    - bit-manipulation
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/bitwise-and-of-numbers-range/)
Given two integers `left` and `right` that represent the range `[left, right]`, return *the bitwise AND of all numbers in this range, inclusive.*


### Examples
**Example 1:**  
```
Input: left = 5, right = 7
Output: 4
```

**Example 2:**  
```
Input: left = 0, right = 0
Output: 0
```

**Example 3:**  
```
Input: left = 1, right = 2147483647
Output: 0
```

### Constraints
+ `0 <= left <= right <= 2^31 - 1`

## Solutions
```cpp
class Solution {
public:
    int rangeBitwiseAnd(int left, int right) {
        if(left == 0 || right == 0) return 0;
        if(left == right) return left;
        if(left == right-1) return left&right;
        if((int)log2(left) != (int)log2(right)) return 0;
        else{
            int ans = left;
            for(int i=left+1;i<=right;i++)
                ans&=i;  
            return ans;    
        }
        
    }
};
```
