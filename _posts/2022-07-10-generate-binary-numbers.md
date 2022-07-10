---
layout: post
title:  Generate Binary Numbers              
summary:
tags:
    - queue
    - geeksforgeeks
    - cpp
    - easy
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/generate-binary-numbers-1587115620/0/?track=DSASP-Queue&batchId=154#)  

Given a number `N`. The task is to generate and print all binary numbers with decimal values from `1` to `N`.


**Your Task:** 
You only need to complete the function `generate()` that takes `N` as parameter and returns vector of strings denoting binary numbers.


**Expected Time Complexity:** `O(N logN)`          
**Expected Auxiliary Space:** `O(N logN)` 


### Examples

**Example 1:**   
```
Input:
N = 5
Output: 
1 10 11 100 101
Explanation: 
Binary numbers from
1 to 5 are 1 , 10 , 11 , 100 and 101. 
```


**Example 2:**   
```
Input:
N = 2
Output: 
1 10
Explanation: 
Binary numbers from
1 to 2 are 1 and 10.

```


### Constraints

+ `1 <= N <= 10^6`

## Solutions

```cpp
//Function to generate binary numbers from 1 to N using a queue.
vector<string> generate(int N)
{
	// Your code here
	queue<string> q;
	q.push("1");
	vector<string> v;
	while(N--){
	    string s = q.front(); q.pop();
	    q.push(s+"0");
	    q.push(s+"1");
	    v.push_back(s);
	}
	return v;
}
```

