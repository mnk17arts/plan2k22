---
layout: post
title: Distinct Difference
summary:
tags:
  - geeksforgeeks
  - array
  - hash
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/c670bf260ea9dce6c5910dedc165aa403f6e951d/1)

Given an array A[] of length N. For each index i (1<=i<=N), find the diffference between the number of distinct element in it's left and right side in the array.

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function getDistinctDifference() which takes the array A[] and its size N as input parameters and returns an array containing the difference between number of ditinct elements in left and right side for each 1<=i<=N.

**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(N)` 

### Examples

**Example 1:**

```
Input:
N = 3
arr[] = {4, 3, 3}
Output: {-1, 0, 2}
Explanation: For index i=1, there are 0 distinct element in the left side of it, and 1 distinct element(3) in it's right side. So difference is 0-1 = -1. 

Similarly for index i=2, there is 1 distinct element (4) in left side of it, and 1 distinct element(3) in it's right side. So difference is 1-1 = 0.

Similarly for index i=3, there are 2 distinct elements (4 and 3) in left side of it, and 0 distinct elements in it's left side. So difference is 2-0 = 2.
```

**Example 2:**

```
Input:
N = 4
arr[] = {4, 4, 3, 3}
Output: {-2, 0, 0, 2}
Explanation: For index i=1, there are 0 distinct element in the left side of it, and 2 distinct element(4 and 3) in it's right side. So difference is 0-2 = -2.

Similarly for index i=2, there is 1 distinct element (4) in left side of it, and 1 distinct element(3) in it's right side. So difference is 1-1 = 0.

Similarly for index i=4, there are 2 distinct elements (4 and 3) in left side of it, and 0 distinct element in it's right side. So difference is 2-0 = 2.
```

### Constraints

- `1 <= N <= 10^5`
- `1 <= arr[i] <= 9`
- Array may contain duplicate elements.

## Solutions

```cpp

class Solution {
  public:
    vector<int> getDistinctDifference(int N, vector<int> &A) {
        // code here
        unordered_set<int> set;
        vector<int> res(N, 0);
        for(int i = 0; i < N; i++) {
            res[i] += set.size();
            set.insert(A[i]);
        }
        set.clear();
        for(int i = N - 1; i >= 0; i--) {
            res[i] -= set.size();
            set.insert(A[i]);
        }
        return res;
    }
};

```
