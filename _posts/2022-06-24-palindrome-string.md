---
layout: post
title: Palindrome String    
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/palindrome-string0817/1#)  

Given a string `S`, check if it is palindrome or not..

**Your Task:** 
You don't need to read input or print anything. Complete the function `isPlaindrome()` which accepts string `S` and returns an integervalue `1` or `0`.


**Expected Time Complexity:** `O(N)` where `N` is length of string `S`.
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input: S = "abba"
Output: 1
Explanation: S is a palindrome
```

**Example 2:**   
```
Input: S = "abc" 
Output: 0
Explanation: S is not a palindrome
```

### Constraints

+ `1 ≤ N <= 10^5`

## Solutions

```cpp
class Solution{
    public:
	int isPalindrome(string S)
	{
	    // Your code goes here
	    for(int i=0; 2*i<S.size(); i++)
	        if(S[i]!=S[S.size()-1-i])
	            return false;
	    return true;
	}
};
```

