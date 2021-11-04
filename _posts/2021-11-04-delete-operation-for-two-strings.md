---
layout: post
title:  Delete Operation for Two Strings
description: 
summary:
tags:
    - string
    - dynamic-programming
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/delete-operation-for-two-strings/)
Given two strings `word`1 and `word2`, return *the minimum number of steps required to make `word1` and `word2` the same.*

In one step, you can **delete** exactly one character in either string.

### Examples

**Example 1:**  
```
Input: word1 = "sea", word2 = "eat"
Output: 2
Explanation: You need one step to make "sea" to "ea" and another step to make "eat" to "ea".
```

**Example 2:**  
```
Input: word1 = "leetcode", word2 = "etco"
Output: 4
```

### Constraints
+ `1 <= word1.length, word2.length <= 500`
+ `word1` and `word2` consist of only lowercase English letters.

## Solutions

```cpp
class Solution {
public:
    int minDistance(string word1, string word2) {
      int m = word1.size();
      int n = word2.size();
      int dp[m+1][n+1];
      for(int i=0; i<m+1; i++) dp[i][0] = i;
      for(int j=1; j<n+1; j++) dp[0][j] = j;
      for(int i=1; i<m+1; i++)
        for(int j=1; j<n+1; j++)
          if(word1[i-1] == word2[j-1])
            dp[i][j] = dp[i-1][j-1];
          else
            dp[i][j] = min(dp[i-1][j], dp[i][j-1]) + 1;
      
      return dp[m][n];
    }
};
```

