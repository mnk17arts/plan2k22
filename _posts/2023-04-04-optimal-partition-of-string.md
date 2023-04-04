---
layout: post
title: Optimal Partition of String
summary:
tags:
  - leetcode
  - string
  - hash
  - cpp
  - medium
minute: 8+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/optimal-partition-of-string/description/)

Given a string s, partition the string into one or more substrings such that the characters in each substring are unique. That is, no letter appears in a single substring more than once.

Return the minimum number of substrings in such a partition.

Note that each character should belong to exactly one substring in a partition.



### Examples

**Example 1:**  

```
Input: s = "abacaba"
Output: 4
Explanation:
Two possible partitions are ("a","ba","cab","a") and ("ab","a","ca","ba").
It can be shown that 4 is the minimum number of substrings needed.
```

**Example 2:**  

```
Input: s = "ssssss"
Output: 6
Explanation:
The only valid partition is ("s","s","s","s","s","s").
```



### Constraints

- `1 <= s.length <= 10^5`
- `s` contains only lowercase English letters.


## Solutions

```cpp

class Solution {
public:
    int partitionString(string s) {
        int last_pos[26] = {}, partitions = 0, last_end = 0;
        for (int i = 0; i < s.length(); i++) {
            if (last_pos[s[i] - 'a'] >= last_end) {
                partitions++;
                last_end = i + 1;
            }
            last_pos[s[i] - 'a'] = i + 1;
        }
        return partitions;
    }
};

```
