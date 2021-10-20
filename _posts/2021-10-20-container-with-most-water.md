---
layout: post
title:  Container With Most Water
description: 
summary: 
tags:
    - pointers
    - string
    - stack
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/container-with-most-water/)
Given `n` non-negative integers `a1, a2, ..., an` , where each represents a point at coordinate (`i, ai`). `n` vertical lines are drawn such that the two endpoints of the line `i` is at (`i, ai`) and (`i, 0`). Find two lines, which, together with the x-axis forms a container, such that the container contains the most water.

**Notice** that you may not slant the container.
 
 
### Examples

**Example 1:**   
<img src="https://s3-lc-upload.s3.amazonaws.com/uploads/2018/07/17/question_11.jpg">
```
Input: height = [1,8,6,2,5,4,8,3,7]
Output: 49
Explanation: The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.
```

**Example 2:**  
```
Input: height = [1,1]
Output: 1
```

**Example 3:**  
```
Input: height = [4,3,2,1,4]
Output: 16
```

**Example 4:**  
```
Input: height = [1,2,1]
Output: 2
```

### Constraints
+ `n == height.length`
+ `2 <= n <= 10^5`
+ `0 <= height[i] <= 10^4`

## Solutions

```cpp

class Solution {
public:
    int maxArea(vector<int>& height) {
        
        int maxWater = 0, curWater = 0;
        int left = 0, right = height.size()-1;
        
        while(left < right){
            
            int minHeight = height[left]>height[right]?right:left;
            
            curWater = (right - left)*height[minHeight];
            
            maxWater = max(maxWater, curWater);
            
            minHeight == left ? left++ : right--;
            
        }
        
        return maxWater;
        
    }
};
```

