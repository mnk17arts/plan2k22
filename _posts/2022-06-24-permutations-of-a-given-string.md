---
layout: post
title: Permutations of a given string   
summary:
tags:
    - string
    - recursion
    - backtracking
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/permutations-of-a-given-string2041/1)  

Given a string `S`. The task is to print all permutations of a given string in lexicographically sorted order.

**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `find_permutaion()` which takes the string S as input parameter and returns a vector of string in lexicographical order.



**Expected Time Complexity:** `O(n! * n)` 
**Expected Auxiliary Space:** `O(n)`

### Examples

**Example 1:**   
```
Input: ABC
Output:
ABC ACB BAC BCA CAB CBA
Explanation:
Given string ABC has permutations in 6 
forms as ABC, ACB, BAC, BCA, CAB and CBA .
```

**Example 2:**   
```
Input: ABSG
Output:
ABGS ABSG AGBS AGSB ASBG ASGB BAGS 
BASG BGAS BGSA BSAG BSGA GABS GASB 
GBAS GBSA GSAB GSBA SABG SAGB SBAG 
SBGA SGAB SGBA
Explanation:
Given string ABSG has 24 permutations.
```

### Constraints

+ `1 <= length of string <= 5`

## Solutions

```cpp
class Solution{
    public:
	    void help(set<string> &s,string S,int i){
	        if(i==S.size()) {s.insert(S); return;}
	        for(int j=i;j<S.size();j++){
	            swap(S[i],S[j]);
	            help(s,S,i+1);
	            swap(S[i],S[j]);
	        }
	    }
		vector<string> find_permutation(string S)
		{
		    // Code here there
		    set<string> s;
		    help(s, S, 0);
		    vector<string> v(s.begin(),s.end());
		    return v;
		}
};
```

