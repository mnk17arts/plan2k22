---
layout: post
title: Magical String
summary:
tags:
  - leetcode
  - 2pointers
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/magical-string/)

A magical string s consists of only '1' and '2' and obeys the following rules:

+ The string s is magical because concatenating the number of contiguous occurrences of characters '1' and '2' generates the string s itself.

The first few elements of s is s = "`1221121221221121122……`". If we group the consecutive 1's and 2's in s, it will be "`1 22 11 2 1 22 1 22 11 2 11 22 ......`" and the occurrences of 1's or 2's in each group are "`1 2 2 1 1 2 1 2 2 1 2 2 ......`". You can see that the occurrence sequence is s itself.

Given an integer n, return the number of 1's in the first n number in the magical string s.

### Examples

**Example 1:**
```
Input: n = 6
Output: 3
Explanation: The first 6 elements of magical string s is "122112" and it contains three 1's, so return 3.
```

**Example 2:**
```
Input: n = 1
Output: 1
```

### Constraints

- `1 <= n <= 10^5`

## Solutions

```cpp

class Solution {
public:
    int magicalString(int n) {
        if(n < 4) {
            return 1;
        }
        vector<int> vec(n + 1);
        vec[0] = 1, vec[1] = 2, vec[2] = 2;
        int left = 2, right = 3, next = 1, res = 1;
        while(right < n) {
            for(int i = 0; i < vec[left]; i++) {
                vec[right] = next;
                if( next == 1 && right < n) {
                    res++;
                }
                right++;
            }
            next ^= 3;
            left++;
        }
        return res;
    }
};

```
