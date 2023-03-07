---
layout: post
title: Longest Common Substring
summary:
tags:
  - geeksforgeeks
  - string
  - dynamic-programming
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/longest-common-substring1452/1)

Given two strings. The task is to find the length of the longest common substring.

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function longestCommonSubstr() which takes the string S1, string S2 and their length n and m as inputs and returns the length of the longest common substring in S1 and S2.

**Expected Time Complexity:** `O(N*M)`  
**Expected Auxiliary Space:** `O(N*M)`

### Examples

**Example 1:**

```
Input: S1 = "ABCDGH", S2 = "ACDGHR", n = 6, m = 6
Output: 4
Explanation: The longest common substring
is "CDGH" which has length 4.
```

**Example 2:**

```
Input: S1 = "ABC", S2 "ACB", n = 3, m = 3
Output: 1
Explanation: The longest common substrings
are "A", "B", "C" all having length 1.
```

### Constraints

- `1 <= n, m <= 1000`

## Solutions

```cpp

class Solution{
  public:
    int longestCommonSubstr (string S1, string S2, int n, int m)  {
        int res = 0;
        vector<vector<int>> dp(n + 1 , vector<int> (m + 1, 0));
        for(int i = 1; i <= n; i++) {
            for(int j = 1; j <= m; j++) {
                if(S1[i - 1] == S2[j - 1]) {
                    dp[i][j] = 1 + dp[i - 1][j - 1];
                }
                res = max(res, dp[i][j]);
            }
        }
        return res;
    }
};

```
