---
layout: post
title: Maximum Length
summary:
tags:
  - geeksforgeeks
  - string
  - cpp
  - medium
minute: 8+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/84963d7b5b84aa24f7807d86e672d0f97f41a4b5/1)

Given the maximum occurrences of a, b, and c in a string. Your task is to make the string containing only a, b, and c such that no three consecutive characters are the same. If the resultant string equals to a+b+c, return the length (a+b+c) otherwise -1.

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function solve( ) which takes integers a, b, and c as input parameters and returns the string length. If there is no possible answer return -1.

**Expected Time Complexity:** `O(a + b + c)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**

```
Input:
a = 3, b = 3, c = 3
Output: 
9
Explanation: 
No three consecutive character of
the string "abcabcabc" is same.
```

**Example 2:**

```
Input:
a = 11, b = 2, c = 2
Output: 
-1
Explanation: 
If we build a string of these character's,
the string will be"aabaacaabaacaaa", here
we can see that there will be three consecutive a. So
there is no solution exist.
```

### Constraints

- `0 ≤ a, b, c  ≤ 10^5`
- `0 < (a + b + c)`

## Solutions

```cpp

class Solution {
  public:
    int solve(int a, int b, int c) {
        vector<int> x = {a, b, c};
        sort(x.begin(), x.end());
        if(x[2]<= 2*(x[0]+x[1]-1)+4 ) {
            return a+b+c;
        }
        return -1;
    }
};

```
