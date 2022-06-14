---
layout: post
title: Numbers containing 1, 2 and 3 
summary:
tags:
    - hash
    - array
    - math
    - geeksforgeeks
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/numbers-containing-1-2-and-32555/0/)  

Given an array `arr[]` of `n` numbers. The task is to print only those numbers whose digits are from set `{1,2,3}`.

**Your Task:** 
Complete `findAll` function and marked satisfied number as '1' in the map mp in range `1` to `1000000`. If no number is marked as satified number `-1` will automatically be printed by the drivers code. The driver code prints the elements in sorted order.


**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input:
n = 3
arr[] = {4,6,7}
Output: -1
Explanation: No elements are there in the 
array which contains digits 1, 2 or 3.
```

**Example 2:**   
```
Input:
n = 4
arr[] = {1,2,3,4}
Output: 1 2 3
Explanation: 1, 2 and 3 are the only 
elements in the array which conatins 
digits as 1, 2 or 3.
```

### Constraints

+ `1 <= N <= 10^6`
+ `1 <= A[i] <= 10^6` 

## Solutions

```cpp
class Solution{
    public:
    //Function to find all the numbers with only 1,2 and 3 in their digits.
    void findAll(int m = 0) {
        //code here
        if( 1<=m && m<=1e6 ) mp[m] = 1;
        else if(m!=0) return;
        findAll(m*10 + 1);
        findAll(m*10 + 2);
        findAll(m*10 + 3);
    }
};
```

