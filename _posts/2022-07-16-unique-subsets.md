---
layout: post
title: Unique Subsets                   
summary:
tags:
    - backtracking
    - recursion
    - sorting
    - geeksforgeeks
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/subsets-1587115621/0?track=DSASP-Backtracking&batchId=154)  

Given an array `arr[]` of integers of size `N` that might contain duplicates, the task is to find all possible unique subsets.

Note: Each subset should be sorted

**Your Task:** 

Your task is to complete the function `AllSubsets()` which takes the array `arr[]` and `N` as input parameters and returns list of all possible unique subsets in lexicographical order. 


**Expected Time Complexity:** `O(2^N)`              
**Expected Auxiliary Space:** `O(X * 2^N)`, `X` = Length of each subset


### Examples

**Example 1:**   
```
Input: N = 3, arr[] = {2,1,2}
Output:(),(1),(1 2),(1 2 2),(2),(2 2)
Explanation: 
All possible subsets = (),(2),(1),(1,2),(2),(2,2),(2,1),(2,1,2)
After Sorting each subset = (),(2),(1),(1,2),(2),(2,2),(1,2),(1,2,2) 
Unique Susbsets in Lexicographical order = (),(1),(1,2),(1,2,2),(2),(2,2)
```

**Example 2:**   
```
Input: N = 4, arr[] = {1,2,3,3}
Output: (),(1),(1 2),(1 2 3)
(1 2 3 3),(1 3),(1 3 3),(2),(2 3)
(2 3 3),(3),(3 3)
```

### Constraints

+ `1 ≤ N <= 12`
+ `1 ≤ arr[i] ≤ 9`

## Solutions

```cpp
class Solution {
  public:
    void AllSubsetsRec(vector<int> arr, int n, int index, vector<vector<int>>& res, vector<int>& sub)
    {
        res.push_back(sub);
        for (int i = index; i < n; ++i)
        {
            sub.push_back(arr[i]);
            AllSubsetsRec(arr, n, i+1, res, sub);
            sub.pop_back();
            while (i+1 < n && arr[i+1] == arr[i])
                ++i;
        }
    }
    //Function to find all possible unique subsets.
    vector<vector<int> > AllSubsets(vector<int> arr, int n) {
        // code here 
        vector<vector<int>> res;
        vector<int> sub;
        sort(arr.begin(), arr.end());
        AllSubsetsRec(arr, n, 0, res, sub);
        return res;
    }
};
```

