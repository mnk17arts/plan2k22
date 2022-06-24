---
layout: post
title: Count the Reversals   
summary:
tags:
    - string
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/count-the-reversals0401/1#)  

Given a string `S` consisting of only opening and closing curly brackets '`{`' and '`}`', find out the minimum number of reversals required to convert the string into a balanced expression.
A reversal means changing '`{`' to '`}`' or vice-versa

**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `countRev()` which takes the string S as input parameter and returns the minimum number of reversals required to balance the bracket sequence. If balancing is not possible, return `-1`. 


**Expected Time Complexity:** `O(N)` 
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
S = "}{{}}{{{"
Output: 3
Explanation: One way to balance is:
"{{{}}{}}". There is no balanced sequence
that can be formed in lesser reversals.
```

**Example 2:**   
```
Input: 
S = "{{}{{{}{{}}{{"
Output: -1
Explanation: There's no way we can balance
this sequence of braces.
```


### Constraints

+ `1 <= N <= 10^5`

## Solutions

```cpp
class Solution{
    public:
    int n=s.size();
    if(n%2)return -1;
    int open=0,close=0,res=0;
    for(int i=0;i<n;i++){
        if(s[i]=='}')
            if(open<=close){res++;open++;}
            else close++;
        else open++;
    }
    return res+abs(open-close)/2;
};
```

