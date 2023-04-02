---
layout: post
title: Array Pair Sum Divisibility Problem
summary:
tags:
  - geeksforgeeks
  - array
  - hash
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/array-pair-sum-divisibility-problem3257/1?page=4&curated[]=1&sortBy=submissions)

Given an array of integers and a number k, write a function that returns true if given array can be divided into pairs such that sum of every pair is divisible by k.

**Your Task:**

You don't need to read or print anything. Your task is to complete the function canPair() which takes array and k as input parameter and returns true if array can be divided into pairs such that sum of every pair is divisible by k otherwise returns false.

**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**

```
Input : arr = [9, 5, 7, 3], k = 6
Output: True
Explanation: {(9, 3), (5, 7)} is a 
possible solution. 9 + 3 = 12 is divisible
by 6 and 7 + 5 = 12 is also divisible by 6.

```

**Example 2:**

```
Input : arr = [2, 4, 1, 3], k = 4
Output: False
Explanation: There is no possible solution.
```

### Constraints

- `1 <= length of array <= 10^5`
- `1 <= elements of array <= 10^5`
- `1 <= k <= 10^5`

## Solutions

```cpp

class Solution {
  public:
    bool canPair(vector<int> nums, int k) {
        if(nums.size()%2!=0)    return false;
        unordered_map<int, int> mp;
        for(auto val: nums)
            mp[val%k]++;
        
        for(auto it: mp){
            int val1 = it.first;
            int val2 = abs(k-it.first);
            
            if(val1==0 and mp[val1]%2==0)
                continue;
            
            if(mp.find(val2)==mp.end()) return false;
            if(mp[val1]!=mp[val2])  return false;
        }
        return true;
    }
};

```
