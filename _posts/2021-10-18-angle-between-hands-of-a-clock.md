---
layout: post
title:  Angle Between Hands of a Clock
description: 
summary: 
tags:
    - leetcode
    - cpp
    - medium
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/angle-between-hands-of-a-clock/)
Given two numbers, hour and minutes. Return the smaller angle (in degrees) formed between the hour and the minute hand.


### Examples   

**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2019/12/26/sample_1_1673.png" width="200"> 
```
Input: hour = 12, minutes = 30
Output: 165
```

**Example 2:**  
<img src="https://assets.leetcode.com/uploads/2019/12/26/sample_2_1673.png" width="200">
```
Input: hour = 3, minutes = 30
Output: 75
```

**Example 3:**  
<img src="https://assets.leetcode.com/uploads/2019/12/26/sample_3_1673.png" width="200">
```
Input: hour = 3, minutes = 15
Output: 7.5
```

**Example 4:**  
```
Input: hour = 4, minutes = 50
Output: 155
```

### Constraints
+ `1 <= hour <= 12`
+ `0 <= minutes <= 59`
+ Answers within `10^-5` of the actual value will be accepted as correct.

## Solutions

```cpp
class Solution {
public:
    double angleClock(int hour, int minutes) {
        if(hour == 12) hour = 0;
        double hr, mr;
        hr = ((double)hour/12)*360 + ((double)minutes/60)*30;
        mr = ((double)minutes/60)*360;
        return abs(hr-mr)<180?abs(hr-mr):360-abs(hr-mr);
    }
};
```

