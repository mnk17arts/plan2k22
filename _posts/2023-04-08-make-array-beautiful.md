---
layout: post
title: Make the Array Beautiful
summary:
tags:
  - geeksforgeeks
  - array
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/badefd58bace4f2ca25267ccfe0c9dc844415e90/1)

Given an array of positive and negative integers. You have to make the array beautiful. An array is beautiful if two adjacent integers, arr[i] and arr[i+1] have the same sign. And you can do the following operation any number of times until the array becomes beautiful.

+ If two adjacent integers have different signs, remove them.

Return the beautiful array after performing the above operation.

Note: An empty array is also a beautiful array. There can be many adjacent integers with different signs. So remove adjacent integers with different signs from left to right.

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function makeBeautiful() which takes an array as an input parameter and returns an array.

**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**

```
Input: 4 2 -2 1
Output: 4 1
Explanation: As at indices 1 and 2 , 2 and -2 have
different sign, they are removed. And the  the final
array is: 4 1.
```

**Example 2:**

```
Input: 2 -2 1 -1
Output: []
Explanation: As at indices 0 and 1, 2 and -2 have
different sign, so they are removed. Now the array
is 1 -1.Now 1 and -1 are also removed as they have
different sign. So the final array is empty. 
```

### Constraints

- `1 <= N ≤ 10^5`
- `-10^5 <= arr[i] <= 10^5`

## Solutions

```cpp

class Solution {
  public:
    vector<int> makeBeautiful(vector<int> arr) {
        int n = arr.size();
        vector<int>ans;
        int i = 0;
        while(i < n){
            if(ans.size() == 0 or (ans.back() >= 0 and arr[i] >= 0)
                or (ans.back() < 0 and arr[i] < 0))
                ans.push_back(arr[i]);
            else
                ans.pop_back();
            i++;
        }
        return ans;
    }
};

```
