---
layout: post
title: Largest number in K swaps                    
summary:
tags:
    - backtracking
    - sorting
    - geeksforgeeks
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/largest-number-in-k-swaps-1587115620/0/?track=DSASP-Backtracking&batchId=154#)  

Given a number `K` and string str of digits denoting a positive integer, build the largest number possible by performing swap operations on the digits of str at most `K` times.

 

**Your Task:** 

You don't have to read input or print anything. Your task is to complete the function `findMaximumNum()` which takes the string and an integer as input and returns a string containing the largest number formed by perfoming the swap operation at most `k` times..


**Expected Time Complexity:** `O(n!/(n-k)!)`  , where `n` = length of input string           
**Expected Auxiliary Space:** `O(n)`


### Examples

**Example 1:**   
```
Input:
K = 3
str = "3435335"
Output:
5543333
Explanation:
Three swaps can make the input
3435335 to 5543333, swapping 3 
with 5, 4 with 5 and finally 3 with 4 
```

**Example 2:**   
```
Input:
K = 4
str = "1234567"
Output:
7654321
Explanation:
Three swaps can make the
input 1234567 to 7654321, swapping 1
with 7, 2 with 6 and finally 3 with 5
```

### Constraints

+ `1 ≤ |str| ≤ 30`
+ `1 ≤ K ≤ 10`


## Solutions

```cpp
class Solution
{
    public:
    void solve(int i,string str,string &res,int n,int k){
        res = max(res,str);
        
        if(i==n || k==0) return;
        
        char mc = str[i];
        for(int j=i+1;j<n;j++) mc=max(mc,str[j]);
        
        if(mc > str[i]) {
            for(int j=i+1; j<n; j++){
                if(str[j]==mc) {
                    swap(str[i],str[j]);
                    solve(i+1,str,res,n,k-1);
                    swap(str[i],str[j]);
                }
            }
        }else solve(i+1,str,res,n,k);
    }
    //Function to find the largest number after k swaps.
    string findMaximumNum(string str, int k) {
       // code here.
       int n = str.size();
       string res = str;
       solve(0,str,res,n,k);
       return res;
    }
};
```

