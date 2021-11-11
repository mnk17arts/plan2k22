---
layout: post
title: Merge Intervals
description: 
summary:
tags:
    - array
    - sorting
    - leetcode
    - cpp
    - medium
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/merge-intervals)  
Given an array of intervals where `intervals[i] = [starti, endi]`, merge all overlapping intervals, and return *an array of the non-overlapping intervals that cover all the intervals in the input.*

### Examples

**Example 1:**    
```
Input: intervals = [[1,3],[2,6],[8,10],[15,18]]
Output: [[1,6],[8,10],[15,18]]
Explanation: Since intervals [1,3] and [2,6] overlaps, merge them into [1,6].
```

**Example 2:**   
```
Input: intervals = [[1,4],[4,5]]
Output: [[1,5]]
Explanation: Intervals [1,4] and [4,5] are considered overlapping.
```

### Constraints
+ `1 <= intervals.length <= 10^4`
+ `intervals[i].length == 2`
+ `0 <= starti <= endi <= 10^4`

## Solutions

```cpp
class Solution {
public:
    vector<vector<int>> merge(vector<vector<int>>& intervals) {
      sort(intervals.begin(), intervals.end());
      vector<vector<int>> res;
      for(auto i: intervals){
        if(res.empty() or res.back()[1] < i[0])
          res.push_back(i);
        else
          res.back()[1] = max(res.back()[1], i[1]);
      }
      return res;
    }
};
```

