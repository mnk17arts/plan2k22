---
layout: post
title: Valid Compressed String
summary:
tags:
  - geeksforgeeks
  - greedy
  - string
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/13eb74f1c80bc67d526a69b8276f6cad1b8c3401/1)

A special compression mechanism can arbitrarily delete 0 or more characters and replace them with the deleted character count.

Given two strings, S and T where S is a normal string and T is a compressed string, determine if the compressed string  T is valid for the plaintext string S

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function checkCompressed() which takes 2 strings S and T as input parameters and returns integer 1 if T is a valid compression of S and 0 otherwise.


**Expected Time Complexity:** `O(|T|)`  
**Expected Auxiliary Space:** `O(1)` 

### Examples

**Example 1:**

```
Input:
S = "GEEKSFORGEEKS"
T = "G7G3S"
Output:
1
Explanation:
We can clearly see that T is a valid 
compressed string for S.
```

**Example 2:**

```
Input:
S = "DFS"
T = "D1D"
Output :
0
Explanation:
T is not a valid compressed string.
```

### Constraints

- `1 ≤ |S| ≤ 10^6`
- `1 ≤ |T| ≤ 10^6`

## Solutions

```cpp

class Solution{
  public:
    int checkCompressed(string s, string t) {
        int i=0,j=0;
        while(i < s.size() and j < t.size()){
            if(s[i] == t[j]) i++,j++;
            else if(isdigit(t[j])){
                int num = 0;
                while(j < t.size() and isdigit(t[j])){
                    num *= 10; num += (t[j++]-'0');
                }
                i += num;
            }
            else return 0;
        }
        return i == s.size() and j == t.size();
    }
};

```
