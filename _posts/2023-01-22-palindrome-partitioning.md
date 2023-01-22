---
layout: post
title: Palindrome Partitioning                       
summary:
tags:
    - leetcode
    - dynamic-programming
    - backtracking
    - cpp
    - medium
minute: 10+ min
---

## Problem Statement - [*link*](https://leetcode.com/problems/palindrome-partitioning/description/)  

Given a string s, partition s such that every substring of the partition is a palindrome. Return all possible palindrome partitioning of s.

### Examples


**Example 1:**   
```
Input: s = "aab"
Output: [["a","a","b"],["aa","b"]]
```


**Example 2:**   
```
Input: s = "a"
Output: [["a"]]
```


### Constraints

+ `1 <= s.length <= 16`
+ `s` contains only lowercase English letters.

## Solutions

```cpp

class Solution {
public:
    int dp[17][17];
    
    bool isValid(string s, int i, int j) {
        if (dp[i][j] != -1) {
            return dp[i][j];
        }
        while (i < j) {
            if (s[i]!=s[j]) {
                return dp[i][j] = false;
            }
            i++;j--;
        }
        return dp[i][j]=true;

    }

    void helper(vector<vector<string>> &res, vector<string> temp, int id, string &s) {
        if (id >= s.length()) {
            res.push_back(temp);
            return ;
        }

        for(int i=id; i<s.length(); i++) {
            if (isValid(s, id, i)) {
                temp.push_back(s.substr(id,i-id+1));
                helper(res, temp, i+1, s);
                temp.pop_back();
            }
        }
        return ;
    }

    vector<vector<string>> partition(string s) {
        memset(dp, -1, sizeof(dp));
        vector<vector<string>> res;
        vector<string> temp;
        helper(res, temp, 0, s);
        return res;
    }
};
```

