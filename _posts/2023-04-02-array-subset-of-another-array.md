---
layout: post
title: Array Subset of another array
summary:
tags:
  - geeksforgeeks
  - array
  - hash
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/array-subset-of-another-array2317/1?page=1&curated[]=1&sortBy=submissions)

Given two arrays: a1[0..n-1] of size n and a2[0..m-1] of size m. Task is to check whether a2[] is a subset of a1[] or not. Both the arrays can be sorted or unsorted. 

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function isSubset() which takes the array a1[], a2[], its size n and m as inputs and return "Yes" if arr2 is subset of arr1 else return "No" if arr2 is not subset of arr1.

**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**

```
Input:
a1[] = {11, 1, 13, 21, 3, 7}
a2[] = {11, 3, 7, 1}
Output:
Yes
Explanation:
a2[] is a subset of a1[]
```

**Example 2:**

```
Input:
a1[] = {10, 5, 2, 23, 19}
a2[] = {19, 5, 3}
Output:
No
Explanation:
a2[] is not a subset of a1[]
```

### Constraints

- `1 <= n,m ≤ 10^5`
- `1 <= a1[i], a2[i] <= 10^6`

## Solutions

```cpp

class Solution {
  public:
  string isSubset(int a1[], int a2[], int n, int m) {
      unordered_map<int,int>mp;
      for(int i=0;i<n;i++){
          mp[a1[i]]++;
      }
      for(int i=0;i<m;i++){
          mp[a2[i]]--;
          if(mp[a2[i]]<0){
              return "No";
          }
      }
      return "Yes";
  }
};

```
