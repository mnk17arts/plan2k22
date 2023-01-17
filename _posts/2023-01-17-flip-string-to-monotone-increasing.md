---
layout: post
title: Flip String to Monotone Increasing                       
summary:
tags:
    - leetcode
    - string
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/flip-string-to-monotone-increasing/description/)  

A binary string is monotone increasing if it consists of some number of 0's (possibly none), followed by some number of 1's (also possibly none).

You are given a binary string s. You can flip s[i] changing it from 0 to 1 or from 1 to 0.

Return the minimum number of flips to make s monotone increasing.


### Examples


**Example 1:**   
```
Input: s = "00110"
Output: 1
Explanation: We flip the last digit to get 00111.
```


**Example 2:**   
```
Input: s = "010110"
Output: 2
Explanation: We flip to get 011111, or alternatively 000111.
```

**Example 3:**
```
Input: s = "00011000"
Output: 2
Explanation: We flip to get 00000000.
```


### Constraints

+ `1 <= s.length <= 10^5`
+ `s[i]` is either `'0'` or `'1'`

## Solutions

```cpp
class Solution {
public:
    int minFlipsMonoIncr(string s) {
        int flipCount = 0;
        int oneCount = 0;
        for(auto c: s){
            if(c=='1') oneCount++;
            else {
                flipCount++;
                flipCount = min(flipCount, oneCount);
            }
        }
        return flipCount;

    }
};
```

