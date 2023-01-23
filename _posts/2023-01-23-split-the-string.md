---
layout: post
title: Split The String                       
summary:
tags:
    - geeksforgeeks
    - string
    - prefix-sum
    - cpp
    - easy
minute: 10+ min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/contest/gfg-weekly-coding-contest-86/problems/)  

Given a string s of length n split them into two strings such that the number of common characters between the two strings are maximized and return the maximum number of common characters.
 

**Your Task:** 

You don't need to read input or print anything. Your task is to complete the function `splitString()` which takes the string `s` as input parameter and returns the maximum number of common characters between the two strings.


### Examples

**Example 1:**   
```
Input :
n=6
s=abccba

Output :
3

Explanation :
Splitting two strings as "abc" and "cba" has atmost 3 distinct characters.
Splitting in "abcc" and "ba" gives only two which is not the maximum.
```

**Example 2:**   
```
Input :
n=5
s=abbdb

Output :
1

Explanation:
Splitting it in "ab" and "bdb" has only 1 character common which is "b"
and it is the maximum.
```

### Constraints

+ `1 <= N <= 10^5`
+ `|S| = N`
+ `S` contains only lowercase English alphabets.

## Solutions

```cpp

class Solution{
	public:

	int splitString(int n,string s)
	{
		//code here
        int left[26]={0},right[26]={0};
        for(int i=0;i<n;i++){
            right[s.at(i)-'a']++;
        }
        int res=INT_MIN;
        for(int i=0;i<n;i++){
          left[s.at(i)-'a']++;
          right[s.at(i)-'a']--;
       
          int cur=0;
          for(int j=0;j<26;j++){
                if( left[j]>0 && right[j]>0)
                cur++;
          }
          res=max(res,cur);
        }
        return res;
	}
};

```

