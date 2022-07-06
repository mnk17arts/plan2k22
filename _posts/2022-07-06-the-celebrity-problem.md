---
layout: post
title: The Celebrity Problem       
summary:
tags:
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/the-celebrity-problem/0/?t#)  

A celebrity is a person who is known to all but does not know anyone at a party. If you go to a party of `N` people, find if there is a celebrity in the party or not.
A square `NxN` matrix `M[][]` is used to represent people at the party such that if an element of row `i` and column `j`  is set to `1` it means ith person knows jth person. Here `M[i][i]` will always be `0`.
**Note**: Follow `0` based indexing.


**Your Task:** 
You don't need to read input or print anything. Complete the function `celebrity()` which takes the matrix `M` and its size `N` as input parameters and returns the index of the celebrity. If no such celebrity is present, return `-1`.

**Expected Time Complexity:** `O(N)` 
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
N = 3
M[][] = {{0 1 0},
         {0 0 0}, 
         {0 1 0}}
Output: 1
Explanation: 0th and 2nd person both
know 1. Therefore, 1 is the celebrity.
```

**Example 2:**   
```
Input:
N = 2
M[][] = {{0 1},
         {1 0}}
Output: -1
Explanation: The two people at the party both
know each other. None of them is a celebrity.
```


### Constraints

+ `2 <= N <= 3000`
+ `0 <= M[][] <= 1`

## Solutions

```cpp
class Solution{
    public:
    //Function to find if there is a celebrity in the party or not.
    int celebrity(vector<vector<int> >& M, int n) 
    {
        // code here 
        int a = 0, b = n-1;
        while(a < b){
            if(M[b][a]) b--;
            else a++;
        }
        for(int i=0; i<n; i++)
            if(i!=a) 
                if(M[i][a]==0 || M[a][i]) return -1;
        return a; 
    }
};
```

