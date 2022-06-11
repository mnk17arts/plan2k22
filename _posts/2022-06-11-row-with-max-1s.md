---
layout: post
title: Row with max 1s 
summary:
tags:
    - matrix
    - array
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/row-with-max-1s0023/1#)  

Given a boolean `2D` array of `n x m` dimensions where each row is sorted. Find the `0`-based index of the first row that has the maximum number of `1`'s.
 

**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `rowWithMax1s()` which takes the array of booleans `arr[][]`, `n` and `m` as input parameters and returns the `0`- based index of the first row that has the most number of `1`s. If no such row exists, return `-1`.

**Expected Time Complexity:** `O(N+M)`  
**Expected Auxiliary Space:** `O(1)` 

### Examples

**Example 1:**   
```
Input: 
N = 4 , M = 4
Arr[][] = {{0, 1, 1, 1},
           {0, 0, 1, 1},
           {1, 1, 1, 1},
           {0, 0, 0, 0}}
Output: 2
Explanation: Row 2 contains 4 1's (0-based
indexing). 
```

**Example 2:**   
```
Input: 
N = 2, M = 2
Arr[][] = {{0, 0}, {1, 1}}
Output: 1
Explanation: Row 1 contains 2 1's (0-based
indexing).
```

### Constraints

+ `1 ≤ N, M ≤ 10^3`
+ `0 ≤ Arr[i][j] ≤ 1`

## Solutions

```cpp
class Solution{
    public:
	int rowWithMax1s(vector<vector<int> > arr, int n, int m) {
	    // code here
	    int i = 0, j = m-1;
	    int res = -1;
	    while( i < n && j >= 0){
	        if(arr[i][j]) { res = i; j-- ; }
	        else i++;
	    }
	    return res;
	}

};
```

