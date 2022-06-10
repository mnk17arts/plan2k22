---
layout: post
title: Number of pairs
summary:
tags:
    - sorting
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/number-of-pairs-1587115620/0/#)  

Given two arrays `X` and `Y` of positive integers, find the number of pairs such that `x^y > y^x` (raised to power of) where `x` is an element from `X` and `y` is an element from `Y`

**Your Task:** 
This is a function problem. You only need to complete the function `countPairs()` that takes `X, Y, M, N` as parameters and returns the total number of pairs.

**Expected Time Complexity:** `O((N+M)logN)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input: 
M = 3, X[] = [2 1 6] 
N = 2, Y[] = [1 5]
Output: 3
Explanation: 
The pairs which follow x^y > y^x are 
as such: 2^1 > 1^2,  2^5 > 5^2 and 6^1 > 1^6 .
```

**Example 2:**   
```
Input: 
M = 4, X[] = [2 3 4 5]
N = 3, Y[] = [1 2 3]
Output: 5
Explanation: 
The pairs for the given input are 
2^1 > 1^2 , 3^1 > 1^3 , 3^2 > 2^3 , 4^1 > 1^4 , 
5^1 > 1^5 .
```

### Constraints

+ `1 <= N,M <= 10^5`
+ `1 <= X[i],Y[i] <= 10^3`

## Solutions

```cpp
class Solution{
    public:
    int count(int x, int Y[], int N, int exp[]){
        if(x==0) return 0;
        if(x==1) return exp[0];
        int* i = upper_bound(Y, Y+N, x);
        int res = (Y+N)-i ;
        res += (exp[0] + exp[1]);
        if(x==2)
            res -= (exp[3] + exp[4]);
        if(x==3)
            res += exp[2];
        return res;
    }
    // X[], Y[]: input arrau
    // M, N: size of arrays X[] and Y[] respectively
    //Function to count number of pairs such that x^y is greater than y^x.
    long long countPairs(int X[], int Y[], int M, int N)
    {
        //Your code here
        int exp[5] = {0};
        for(int i=0; i<N; i++)
           if(Y[i] < 5) exp[Y[i]]++;
        sort(Y, Y+N);
        long long res = 0;
        for(int i=0; i<M; i++)
            res += count(X[i], Y, N, exp);
        return res;
    }

};
```

