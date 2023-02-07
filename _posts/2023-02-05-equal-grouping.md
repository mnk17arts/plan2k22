---
layout: post
title: Equal grouping
summary:
tags:
    - geeksforgeeks
    - array
    - stack
    - cpp
    - medium
minute: 10+ min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/contest/gfg-weekly-coding-contest-88/problems/#)

Let us group integers on the number line. Let's call integers in the range [2^i, 2^(i+1)-1] (both ends inclusive) for 0 <= i <= 30 in the same group. 

You are given an array of A of N elements. In one operation you can select any suarray of even size such that all integers in the subarray belong to the same group and delete that subarray.

After deleting join the remaining subarrays without changing the order. Find the minimum size of A after performing the above operation any number of times.

**Your Task:** 

The task is to complete the function `equalGrouping()` which takes an array A and its size N as input parameters and returns the minimum size of A after performing the above operation any number of times.


### Examples

**Example 1:**   
```
Input: 
N = 4,
A = { 7, 8, 6, 4  }
Output:
2
Explanation:
Since 4 and 6 belongs to the same
group we can remove them in one
step and after that we can't
perform any step because 7 and
8 belongs to different groups.
```

**Example 2:**   
```
Input:
N = 3,
A = { 1, 7, 2 }
Output:
3
Explanation:
No operations can be performed.
```

### Constraints

+ `1 ≤ N ≤ 10^5`
+ `1 ≤ A[i] ≤ 10^9`

## Solutions

```cpp

class Solution{
	public:
	int evenGrouping(int n,int a[])
	{
		//code here
        stack<int> st;
        for(int i=0; i<n; i++) {
            a[i] = log2(a[i]);
        }
        for(int i=0; i<n; i++) {
            if( !st.empty() && st.top()==a[i] ) {
                st.pop();
            }
            else {
                st.push(a[i]);
            }
        }
		return st.size();
	}
};

```
