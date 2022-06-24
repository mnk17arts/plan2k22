---
layout: post
title: Longest Palindrome in a String    
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/longest-palindrome-in-a-string3411/1#)  

Given a string `S`, find the longest palindromic substring in `S`. Substring of string `S`: `S[ i . . . . j ]` where `0` ≤ `i` ≤ `j` < `len(S)`. Palindrome string: A string which reads the same backwards. More formally, `S` is palindrome if reverse(`S`) = `S`. Incase of conflict, return the substring which occurs first ( with the least starting index).

**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `longestPalin()` which takes the string `S` as input and returns the longest palindromic substring of `S`

**Expected Time Complexity:** `O(N^2)` where `N` is length of string `S`.
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
S = "aaaabbaa"
Output: aabbaa
Explanation: The longest Palindromic
substring is "aabbaa".
```

**Example 2:**   
```
Input: 
S = "abc"
Output: a
Explanation: "a", "b" and "c" are the 
longest palindromes with same length.
The result is the one with the least
starting index.
```

### Constraints

+ `1 ≤ N <= 10^3`

## Solutions

```cpp
class Solution{
    public:
    string longestPalin (string S) {
        // code here
        int n=S.size(),i,start=0,len=1,left,right;
        for(i=1; i<n; i++){
            // even
            left = i-1; right = i;
            while(left>=0 && right<n && S[left]==S[right]){
                if(len < right-left+1) { len =right-left+1; start=left; }
                left--; right++;
            }
            // odd
            left = i-1; right = i+1;
            while(left>=0 && right<n && S[left]==S[right]){
                if(len < right-left+1) { len =right-left+1; start=left; }
                left--; right++;
            }
        }
        return S.substr(start,len);
    }
};
```

