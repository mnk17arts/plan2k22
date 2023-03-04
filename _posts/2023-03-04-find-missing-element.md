---
layout: post
title: Find Missing And Repeating
summary:
tags:
  - geeksforgeeks
  - array
  - hash
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/find-missing-and-repeating2512/1)

Given an unsorted array Arr of size N of positive integers. One number 'A' from set {1, 2, N} is missing and one number 'B' occurs twice in array. Find these two numbers.

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function findTwoElement() which takes the array of integers arr and n as parameters and returns an array of integers of size 2 denoting the answer ( The first index contains B and second index contains A.)

**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**

```
Input:
N = 2
Arr[] = {2, 2}
Output: 2 1
Explanation: Repeating number is 2 and 
smallest positive missing number is 1.
```

**Example 2:**

```
Input:
N = 3
Arr[] = {1, 3, 3}
Output: 3 2
Explanation: Repeating number is 3 and 
smallest positive missing number is 2.
```

### Constraints

- `2 ≤ N  <= 10^5`
- `1 ≤ Ai  <= N`

## Solutions

```cpp

class Solution{
    public:
    int *findTwoElement(int *arr, int n) {
        unordered_map<int, int> map;
        for(int i = 0; i < n; i++) {
            map[arr[i]]++;
        }
        int *res = new int[2];
        for(int i = 1; i <= n; i++) {
            if(map.find(i) == map.end()) {
                res[1] = i;
            }
            else if(map[i] == 2) {
                res[0] = i;
            }
        }
        return res;
    }
};

```
