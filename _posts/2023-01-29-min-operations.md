---
layout: post
title: Min operations                     
summary:
tags:
    - geeksforgeeks
    - math
    - cpp
    - easy
minute: 5+ min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/5a7e1a52f1b7796238f9efea4c6fda389f26c327/1)  

Given two numbers a and b. In one operation you can pick any non negative integer x and either of a or b. Now if you picked a then replace a with a&x else if you picked b then replace b with b&x.

Return the minimum number of operation required to make a and b equal.

Note: Here & represents bitwise AND operation.

**Your Task:** 

You don't need to read, input, or print anything. Your task is to complete the function solve( ), which takes two integers a and b as input parameters and returns the answer.



**Expected Time Complexity:** `O(1)`              
**Expected Auxiliary Space:** `O(1)` 



### Examples

**Example 1:**   
```
Input:
a = 5, b = 12
Output:
2
Explanantion:
In first operation replace 
a = a&4 = 4
after that replace 
b = b&6 = 4
Hence both are same after applying two
operations.
```

**Example 2:**   
```
Input: 
a = 100, b = 100
Output: 
0
Explanation: 
Already same.
```

### Constraints

+ `0 ≤ a, b ≤ 10^9`

## Solutions

```cpp

class Solution{
  public:
    int solve(int a, int b) {
        // code here
        int x = a&b;
        int res = 0;
        if(x != a) {
            res++;
        } 
        if(x != b) {
            res++;
        }
        return res;
    }
};

```

