---
layout: post
title: Add minimum characters
summary:
tags:
  - geeksforgeeks
  - string
  - cpp
  - medium
minute: 8+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/3d49e4cce2820a813da02d1587c2dd9c542ce769/1)

Given a string str, find the minimum characters to be added at front of the string to make it a palindrome.

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function addMinChar() which takes the string str as input parameters and returns the minimum number of characters to be added to make it a palindrome.

**Expected Time Complexity:** `|str|`  
**Expected Auxiliary Space:** `|str|`

### Examples

**Example 1:**

```
Input:
str = ABCD
Output: 3
Explanation: The resultant string 
after adding 3 characters is DCBABCD.
The minimum possible answer is 3.
```

**Example 2:**

```
Input:
str = ABA
Output: 0
Explanation: The given string
is already a palindrome.
```

### Constraints

- `1 <= |str| ≤ 10^5`
- `str` contains only uppercase English alphabets.

## Solutions

```cpp

class Solution {
  public:
    int addMinChar(string str){    
        int n=str.length();
        int i=0,j=n-1;
        int ans=0;
        while(i<=j)
        {
            if(str[i]==str[j])
            {
                i++;
                j--;
            }
            else
            {
                ans++; // adding one character at the front
                i=0;
                j=n-1-ans;
            }
        }
        return ans; 
    }
};

```
