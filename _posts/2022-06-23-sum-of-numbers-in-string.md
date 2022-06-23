---
layout: post
title: Sum of numbers in string 
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/sum-of-numbers-in-string-1587115621/0/?)  

Given a string `str` containing alphanumeric characters. The task is to calculate the sum of all the numbers present in the string.

**Your Task:** 
The task is to complete the function `findSum()` which finds and returns the sum of numbers in the string.


**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input:
str = 1abc23
Output: 24
Explanation: 1 and 23 are numbers in the
string which is added to get the sum as
24.
```

**Example 2:**   
```
Input:
str = geeks4geeks
Output: 4
Explanation: 4 is the only number, so the
sum is 4.
```

### Constraints

+ `1 <= length of the string <= 10^5`
+ `Sum of Numbers <= 10^5`

## Solutions

```cpp
class Solution{
    public:
    //Function to calculate sum of all numbers present in a string.
    int findSum(string str)
    {
    	
    	// Your code here
    	int num = 0, sum = 0;
    	for(int i=0; i<str.size(); i++){
    	    if( '0' <= str[i] && str[i] <= '9')
    	        num = num*10 + (str[i]-'0') ;
    	    else { sum += num; num = 0; }
    	}
    	sum+=num;
    	return sum;
    	
    }
};
```

