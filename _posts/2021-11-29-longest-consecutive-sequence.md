---
layout: post
title:  Longest Consecutive Sequence
summary:
tags:
    - leetcode
    - cpp
    - medium
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/longest-consecutive-sequence)  

Given an unsorted array of integers `nums`, return *the length of the longest consecutive elements sequence.*

You must write an algorithm that runs in `O(n)` time.

### Examples

**Example 1:**   
```
Input: nums = [100,4,200,1,3,2]
Output: 4
Explanation: The longest consecutive elements sequence is [1, 2, 3, 4]. Therefore its length is 4.
```

**Example 2:**    
```
Input: nums = [0,3,7,2,5,8,4,6,0,1]
Output: 9
```

### Constraints
+ `0 <= nums.length <= 10^5`
+ `-10^9 <= nums[i] <= 10^9`

## Solutions

```cpp
class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
      set<int> s;
      for(auto x: nums) s.insert(x);
      int res = 0;
      for(auto i: s)
        if(s.find(i-1)==s.end()){
          int x = i;
          int temp = 1;
          while(s.find(x+1)!=s.end()){
            x+=1; temp+=1;
          }
          res = max(res, temp);
        }
      
      return res;
    }
};
```

