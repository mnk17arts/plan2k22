---
layout: post
title: Check if a String is Subsequence of Other    
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/given-two-strings-find-if-first-string-is-a-subsequence-of-second/0/?track=DSASP-Strings&batchId=154#)  

Given two strings `A` and `B`, find if `A` is a subsequence of `B`. A subsequence is a sequence that can be derived from another sequence by deleting some elements without changing the order of the remaining elements.



**Your Task:** 
You dont need to read input or print anything. Complete the function `isSubSequence()` which takes `A` and `B` as input parameters and returns a boolean value denoting if `A` is a subsequence of `B` or not. 


**Expected Time Complexity:** `O(N)` where `N` is length of string `B`.
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
A = AXY 
B = YADXCP
Output: False
Explanation: A is not a subsequence of B
as 'Y' appears before 'A'.
```

**Example 2:**   
```
Input:
A = gksrek
B = geeksforgeeks
Output: True
Explanation: A is a subsequence of B.
```

### Constraints

+ `1 ≤ |A|,|B|<= 10^6`

## Solutions

```cpp
class Solution{
    public:
    //Function to check if a string is subsequence of other string.
    bool isSubSequence(string A, string B)
    {
        //code here
        int n=A.size(),m=B.size();
        int i=0,j=0;
        while(i<n&&j<m){
            if(A[i]==B[j]){i++;j++;}
            else j++; 
            if(i==n) return true;
        }

        return false;
        
    }
};
```

