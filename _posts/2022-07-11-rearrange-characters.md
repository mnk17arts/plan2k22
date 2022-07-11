---
layout: post
title: Rearrange characters               
summary:
tags:
    - heap
    - string
    - priority-queue
    - queue
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/rearrange-characters5322/0/?track=DSASP-Heap&batchId=154#)  

Given a string `S` such that it may contain repeated lowercase alphabets. Rearrange the characters in the string such that no two adjacent characters are same.

**Your Task:** 
You do not need to read input or print anything. Complete the function `rearrangeString()` which takes string `S` as input parameter and returns the string after rearrangement.
If the characters are successfully rearranged then the generated output will be `1` else `0`.



**Expected Time Complexity:** `O(|S| log |S|)`           
**Expected Auxiliary Space:** `O(1)`


### Examples

**Example 1:**   
```
Input:
S = geeksforgeeks
Output: 1
Explanation: egeskerskegof can be one way of
rearranging the letters.
``` 


**Example 2:**   
```
Input:
S = bbbabaaacd
Output: 1
Explanation: abababdcab can be one way of 
rearranging the letters.
```


### Constraints

+ `1 <= |S| <= 10^5`
+ `S` consists of lowercase alphabets only.

## Solutions

```cpp
class Solution
{
    public:
    //Function to rearrange the characters in a string such that 
    //no two adjacent characters are same.
    string rearrangeString(string str)
    {
    	// Your code here
    	int carr[26] = {0};
    	for(auto c: str) carr[c-'a']++;
    	priority_queue<pair<int,char>> pq;
    	for(int i=0; i<26; i++)
    	    if(carr[i]) pq.push({carr[i],'a'+i});
    	str = "";
    	auto pre = pq.top(); pq.pop();
    	str += pre.second;
    	pre.first--;
    	while(!pq.empty()){
    	    auto cur = pq.top(); pq.pop();
    	    str += cur.second;
    	    if(pre.first) pq.push(pre);
    	    cur.first--;
    	    pre = cur;
    	}
    	return str;
    }  
};
```

