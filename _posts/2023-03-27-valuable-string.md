---
layout: post
title: Valuable String
summary:
tags:
  - geeksforgeeks
  - array
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/contest/gfg-weekly-coding-contest-95/problems/)

You are given an array arr of n strings. The strings consist of lowercase Latin letters. The value of each string is defined as the difference between the number of consonants and vowels. You have to find the string with the maximum value. If there is a tie between some strings, the first one should be returned.

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function valuableString() which takes an integer n, and an array arr[] as input parameters and returns the maximum valued string.

### Examples

**Example 1:**

```
Input:
n = 3
arr = {"house","car","tree"}
Output:
"house"
Explanation:
The strings "house" and "car" both have value 1. So, "house" should be answer.
```

**Example 2:**

```
Input:
n = 3
arr={"geeksforgeeks","interview","series"}
Output:
"geeksforgeeks"
Explanation:
The value of "geeksforgeeks" is 3, and it is the maximum.
```

### Constraints

- `1 ≤ n ≤ 10^4`
- `1 ≤ |arr[i]| ≤ 10^3`
- Sum of length of all strings is at most `10^7`

## Solutions

```cpp

class Solution {
    int util(string str) {
        int res = 0;
        for(char c: str) {
            if(c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u') {
                res++;
            }
            else {
                res--;
            }
        }
        return abs(res);
    }
  public:
    string valuableString(int n, vector<string> &arr) {
        // code here
        int resID = -1;
        int maxVal = INT_MIN;
        for(int i = 0; i < n; i++) {
            int curVal = util(arr[i]);
            if(maxVal < curVal) {
                maxVal = curVal;
                resID = i;
            }
        }
        return arr[resID];
    }
};


```
