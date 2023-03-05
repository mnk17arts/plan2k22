---
layout: post
title: Save Flowers
summary:
tags:
  - geeksforgeeks
  - array
  - string
  - 2pointers
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/contest/gfg-weekly-coding-contest-92/problems#)

Geek is selling flowers at the fair. He distributed all the flowers in n baskets kept in a row. You are given an array arr of n elements, where the ith box contains arr[i] flowers. And you are also given a string s, where s[i] denotes if the box has a lid or not.

Suddenly it started to rain, and geek have to save as many flowers as possible. If an ith box has a lid, he can transfer the lid to the (i-1)th box, if that box has no lid. The transfer takes no time. Your task is to determine the maximum number of flowers that can be saved from rainfall. You can't move a lid more than once.

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function saveFlowers() which takes an integer n, an array arr[], and a string s as input parameters and returns the maximum number of flowers that can be saved.

**Expected Time Complexity:** `O(n)`  
**Expected Auxiliary Space:** `O(n)`

### Examples

**Example 1:**

```
Input:
n = 5
arr = {3,5,2,9,1}
s = "00110"
Output:
14
Explanation:
Geek can move the 3rd lid to the 2nd box, thus the number of flowers that can be saved is (9+5)=14.
```

**Example 2:**

```
Input:
n = 3
arr = {2,1,3}
s = "000"
Output:
0
Explanation:
Geek has no lid to protect the flowers.
```

### Constraints

- `1 ≤ N  <= 10^4`
- `1 ≤ arr[i] ≤ 10^3`
- `s` contains only '0' and '1'

## Solutions

```cpp

class Solution{
  public:
    int saveFlowers(int n, vector<int> &arr, string s) {
        int res = 0;
        for(int i = 0; i < n; i++) {
            if(s[i] == '1') {
                res += arr[i];
            }
        }
        for(int i = n - 1; i > 0; i--) {
            if(s[i] == '1') {
                int j = i - 1;
                int cur = arr[i], me = arr[i];
                while(j > 0 && s[j] == '1') {
                    cur += arr[j];
                    me = min(me, arr[j]);
                    j--;
                }
                if(s[j] == '0') {
                    me = min(me, arr[j]);
                    res -= cur;
                    cur += arr[j];
                    cur -= me;
                    res += cur;
                }
                i = j;
            }
        }
        return res;
    }
};

```
