---
layout: post
title: Daily Temperatures
description: 
summary:
tags:
    - array
    - stack
    - leetcode
    - cpp
    - medium
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/daily-temperatures)  
Given an array of integers `temperatures` represents the daily `temperatures`, return an array `answer` such that `answer[i]` is the number of days you have to wait after the `ith` day to get a warmer temperature. If there is no future day for which this is possible, keep `answer[i] == 0` instead.

### Examples

**Example 1:**    
```
Input: temperatures = [73,74,75,71,69,72,76,73]
Output: [1,1,4,2,1,1,0,0]
```

**Example 2:**   
```
Input: temperatures = [30,40,50,60]
Output: [1,1,1,0]
```

**Example 3:**   
```
Input: temperatures = [30,60,90]
Output: [1,1,0]
```

**Example 4:**   
```
Input: nums = [0]
Output: 1
Explanation: n = 1 since there is 1 number, so all numbers are in the range [0,1]. 1 is the missing number in the range since it does not appear in nums.
```

### Constraints
+ `1 <= temperatures.length <= 10^5`
+ `30 <= temperatures[i] <= 100`

## Solutions

```cpp
class Solution {
public:
    vector<int> dailyTemperatures(vector<int>& temperatures) {
      int n = temperatures.size();
      vector<int> res(n);
      stack<int> q;
      for(int i=0; i<n; i++){
        int j = temperatures[i];
        while( !q.empty() and temperatures[q.top()] < j ){
          int l = q.top();
          q.pop();
          res[l] = i - l;
        }
        q.push(i);
      }
      return res;
    }
};
```

