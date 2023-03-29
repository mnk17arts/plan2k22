---
layout: post
title: Count the substrings
summary:
tags:
  - geeksforgeeks
  - string
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/839d6ba2c2e4c669ba9d9d9f32ad20118937284e/1)

Given a string S. The task is to count the number of substrings which contains equal number of lowercase and uppercase letters. 

**Your Task:**

The task is to complete the function countSubstring() which takes the string S as input parameter and returns the number of substrings which contains equal number of uppercase and lowercase letters.

**Expected Time Complexity:** `O(N*N)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**

```
Input:
S = "gEEk"
Output: 3
Explanation: There are 3 substrings of
the given string which satisfy the
condition. They are "gE", "gEEk" and "Ek".
```

**Example 2:**

```
Input:
S = "WomensDAY"
Output: 4
Explanation: There are 4 substrings of 
the given string which satisfy the
condition. They are "Wo", "ensDAY", 
"nsDA" and "sD"
```

### Constraints

- `1 ≤ |S| ≤  10^73`

## Solutions

```cpp

class Solution{
    public:
    int countSubstring(string str) {
        // code here
        unordered_map<int, int> map;
        map[0] = 1;
        int res = 0, sum = 0;
        for(char c: str) {
            sum += (isupper(c) ? 1 : -1);
            if(map.find(sum) != map.end()) {
                res += map[sum];
            }
            map[sum]++;
        }
        return res;
    }
};

```
