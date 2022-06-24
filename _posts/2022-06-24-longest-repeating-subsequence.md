---
layout: post
title: Longest Repeating Subsequence   
summary:
tags:
    - string
    - dynamic-programming
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/longest-repeating-subsequence2004/1)  

Given a string `str`, find the length of the longest repeating subsequence such that it can be found twice in the given string. The two identified subsequences `A` and `B` can use the same `i`th character from string str if and only if that `i`th character has different indices in `A` and `B`.

**Your Task:** 
You don't need to read or print anything. Your task is to complete the `LongestRepeatingSubsequence()` which takes str as input parameter and returns the length of the longest repeating subsequnece.



**Expected Time Complexity:** `O(N^2)` where `N` is length of string `S`.
**Expected Auxiliary Space:** `O(N^2)`

### Examples

**Example 1:**   
```
Input:
str = "axxzxy"
Output: 2
Explanation:
The given array with indexes looks like
a x x z x y 
0 1 2 3 4 5

The longest subsequence is "xx". 
It appears twice as explained below.

subsequence A
x x
0 1  <-- index of subsequence A
------
1 2  <-- index of str 


subsequence B
x x
0 1  <-- index of subsequence B
------
2 4  <-- index of str 

We are able to use character 'x' 
(at index 2 in str) in both subsequences
as it appears on index 1 in subsequence A 
and index 0 in subsequence B.
```

**Example 2:**   
```
Input:
str = "axxxy"
Output: 2
Explanation:
The given array with indexes looks like
a x x x y 
0 1 2 3 4

The longest subsequence is "xx". 
It appears twice as explained below.

subsequence A
x x
0 1  <-- index of subsequence A
------
1 2  <-- index of str 


subsequence B
x x
0 1  <-- index of subsequence B
------
2 3  <-- index of str 

We are able to use character 'x' 
(at index 2 in str) in both subsequences
as it appears on index 1 in subsequence A 
and index 0 in subsequence B.
```

### Constraints

+ `1 ≤ N <= 10^3`

## Solutions

```cpp
class Solution{
    public:
		int LongestRepeatingSubsequence(string str){
		    // Code here
		    int n=str.size(),dp[n+1][n+1];
		    for(int i=0;i<n+1;i++)
		        for(int j=0;j<n+1;j++)
		            if(i==0||j==0) dp[i][j]=0;
		            else if(str[i-1]==str[j-1]&&i!=j) dp[i][j]=1+dp[i-1][j-1];
		            else dp[i][j]=max(dp[i-1][j],dp[i][j-1]);
		    return dp[n][n];
		}
};
```

