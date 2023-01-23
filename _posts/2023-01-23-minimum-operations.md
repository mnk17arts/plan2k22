---
layout: post
title: Minimum Operations                       
summary:
tags:
    - geeksforgeeks
    - string
    - prefix-sum
    - cpp
    - medium
minute: 10+ min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/contest/gfg-weekly-coding-contest-86/problems/)  

Given an array arr of size n, make the array in minimum number of operations.
An array is called special if all elements are equal.
An opeartion is defined as take any subarray of size<=3 and replace that with it's maximum element.


**Your Task:** 

You don't need to read input or print anything. Your task is to complete the function `minOperations()` which takes the array `arr` and it's size `n` as input parameter and returns the minimum number of operations required to make the array special.

### Examples

**Example 1:**   
```
Input :
6
1 2 7 2 2 7

Output:
2

Explaination :
In operation 1 :- we can 1 2 7 and replace with 7.
In operation 2 :- we can take 2 2 7 and replace with 7.
Remaining array is 7 7 which is special.
```

**Example 2:**   
```
Input:
5
1 2 7 2 7

Output :
2

Explaination :
In one operation you can take 1 2 7 and replace it with 7 .
Now array becomes 7 2 7 . So you can take 7 2 7 as subarray and replace 
it with 7 . Note that you can take 2 7 as well in one operation.
```

### Constraints

+ `1 <= N <= 10^6`
+ `1 <= arr[i] <= 10^4`


## Solutions

```cpp

class Solution{
	public:
	int minimumOperations(int n,vector<int> &arr)
	{
		//code here
        // finding max of the arr for simplification 		
		int max = *max_element(arr.begin(), arr.end());
        // converting the arr into binary array	
		for(int &i: arr) {
		    i = (i==max);
		}
        //  result , current group, 0s count last time (odd or even), 1s count 		
		int res=0, cur=arr.back(), prev=0, plen=0;
		while( arr.size() ) {
		    int count = 0;
		    while( arr.size() && arr.back()==cur ) {
		        count++;
		        arr.pop_back();
		    }
		    if(cur==0) {
		      // no. of 0 pairs..  
		        res += (count+1)/2;
		      //  1. if prev 0 is of odd or even count.
		      //  2. if current 0 is of odd or even count.
		      //  3. length of 1 must be 1.
		      // ex: .0001000.
		      if(prev && count%2 && plen==1) {
		          res--;
		          prev = 0;
		          plen = 0;
		      }
		      else {
		          prev = count%2; // if this group contains odd 0s (useful in future operations)
		      }
		        
		    }
		    else {
		        plen = count; // count of 1s (used in 0 groups)
		    }
		    cur ^= 1; // changing groups
		}
		return res;
	}
};

```

