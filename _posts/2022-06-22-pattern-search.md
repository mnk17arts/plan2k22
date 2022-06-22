---
layout: post
title: Pattern Search   
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/distinct-pattern-search-1587115620/0/?track=DSASP-Strings&batchId=154#)  

Given a string `S` and a pattern `P` both of lowercase characters. The task is to check if the given pattern exists in the given string or not.


**Your Task:** 
The task is to complete the function `search()` which finds the pattern in the given string. The function takes pattern and string as parameters and returns either `true` or `false`. Return `true` if pattern exists else return `false`.


**Expected Time Complexity:** `O(n+m)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
S = aabaacaadaabaaabaa
P = aaba
Output: Yes
Explanation: Given pattern aaba is found
in the string at index 0.
```

**Example 2:**   
```
Input:
S = aabaacaadaabaaabaa
P = ccda
Output: No
Explanation: Given pattern ccda doesn't
exists in the string at all.
```

### Constraints

+ `1 <= |S|, |P| <= 10^3`

## Solutions

```cpp
class Solution{
    public:
    //Function to check if the given pattern exists in the given string or not.
    bool search(string pat, string txt) 
    { 
    	
    	// Your code here
    	int j = 0;
    	for(int i=0; i<txt.size(); i++){
    	    if(txt[i] == pat[j]) j++;
    	    else { j=0; if(txt[i] == pat[j]) j++; }
    	    if(j==pat.size()) return true;
    	}
    	return false;
    	
    }
};
```

