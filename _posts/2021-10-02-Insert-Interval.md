---
layout: post
title: Insert new interval in the given intervals
description: Insert newInterval into intervals such that intervals is still sorted in ascending order by starti and intervals still does not have any overlapping intervals (merge overlapping intervals if necessary).
summary: 
tags:
    - array
    - leetcode
    - cpp
    - medium
minute: 1
---

## Problem Statement - [*link*](https://leetcode.com/problems/insert-interval/)
You are given an array of non-overlapping intervals `intervals` where `intervals[i] = [starti, endi]` represent the start and the end of the `ith` interval and `intervals` is sorted in ascending order by `starti`. You are also given an interval `newInterval = [start, end]` that represents the start and end of another interval.

Insert `newInterval` into `intervals` such that `intervals` is still sorted in ascending order by `starti` and `intervals` still does not have any overlapping intervals (merge overlapping intervals if necessary).

Return `intervals` after the insertion.

### Examples
**Example 1:**
```
Input: intervals = [[1,3],[6,9]], newInterval = [2,5]
Output: [[1,5],[6,9]]
```

**Example 2:**
```
Input: intervals = [[1,2],[3,5],[6,7],[8,10],[12,16]], newInterval = [4,8]
Output: [[1,2],[3,10],[12,16]]
Explanation: Because the new interval [4,8] overlaps with [3,5],[6,7],[8,10].
```
**Example 3:**
```
Input: intervals = [], newInterval = [5,7]
Output: [[5,7]]
```
**Example 4:**
```
Input: intervals = [[1,5]], newInterval = [2,3]
Output: [[1,5]]
```
**Example 5:**
```
Input: intervals = [[1,5]], newInterval = [2,7]
Output: [[1,7]]
```

### Constraints
+ `0 <= intervals.length <= 10^4`
+ `intervals[i].length == 2`
+ `0 <= starti <= endi <= 10^5`
+ `intervals` is sorted by `starti` in ascending order.
+ `newInterval.length == 2`
+ `0 <= start <= end <= 10^5`

## Solution
```cpp
class Solution {
public:
    vector<vector<int>> insert(vector<vector<int>>& intervals, vector<int>& newInterval) {
        vector<vector<int>> mnk;
        int i= newInterval[0], j= newInterval[1];
        bool flag = false;
        for(int k=0; k < intervals.size() ; k++){
            if(intervals[k][1] < i){
                mnk.push_back(intervals[k]);
            }else if(intervals[k][0] > j){
                if(!flag){
                    mnk.push_back({i,j});
                    flag = true;
                }
                mnk.push_back(intervals[k]);
            }else{
                i = min(i,intervals[k][0]);
                j = max(j,intervals[k][1]);
            }
        }
        if(!flag){
            mnk.push_back({i,j});
        }
        return mnk;
        
    }
};
```