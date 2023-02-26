---
layout: post
title: Find the Divisibility Array of a String
summary:
tags:
  - leetcode
  - array
  - math
  - cpp
  - medium
minute: 8+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/find-the-divisibility-array-of-a-string/description/)

You are given a 0-indexed string word of length n consisting of digits, and a positive integer m.

The divisibility array div of word is an integer array of length n such that:

+ div[i] = 1 if the numeric value of word[0,...,i] is divisible by m, or
+ div[i] = 0 otherwise.

Return the divisibility array of word.

### Examples

**Example 1:**  
```
Input: word = "998244353", m = 3
Output: [1,1,0,0,0,1,1,0,0]
Explanation: There are only 4 prefixes that are divisible by 3: "9", "99", "998244", and "9982443".
```

**Example 2:**  
```
Input: word = "1010", m = 10
Output: [0,1,0,1]
Explanation: There are only 2 prefixes that are divisible by 10: "10", and "1010".
```


### Constraints

- `1 <= n <= 10^5`
- `word` consists of digits.
- `1 <= m <= 10^9`

## Solutions

```cpp

class Solution {
public:
    vector<int> divisibilityArray(string word, int m) {
        long long cur = 0;
        vector<int> res;
        for(char &c: word) {
            cur *= 10;
            cur += (c - '0');
            if(cur % m == 0) {
                res.push_back(1);
            }
            else {
                res.push_back(0);
            }
            cur %= m;
        }
        return res;
    }
};

```
