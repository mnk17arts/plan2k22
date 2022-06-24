---
layout: post
title: Split the binary string into substrings with equal number of 0s and 1s   
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - medium
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/split-the-binary-string-into-substrings-with-equal-number-of-0s-and-1s/1/)  

Given binary string `str` of length `N`. The task is to find the maximum count of consecutive substrings `str` can be divided into such that all the substrings are balanced i.e. they have an equal number of `0`s and `1`s. If it is not possible to split `str` satisfying the conditions then return `-1`.

**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `maxSubStr()` which takes a string S and returns an integer as output.



**Expected Time Complexity:** `O(N)` 
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
S = "0100110101"
Output: 4
Explanation: 
The required substrings are 01, 0011, 01 and 01.
```

**Example 2:**   
```
Input:
S = "0111100010"
Output: 3
```

### Constraints

+ `1 <= length of string <= 10^5`

## Solutions

```cpp
class Solution{
    public:
    int maxSubStr(string str){
        //Write your code here
        int check=0,res=0;
        for(char c: str){
            if(c=='0') check--;
            else check++;
            if(check==0) res++;
        }
        if(check!=0) return -1;
        return res;
    }
};
```

