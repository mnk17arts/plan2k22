---
layout: post
title: Type it!                       
summary:
tags:
    - Total Decoding Messages
    - string
    - dynamic-programming
    - cpp
    - medium
minute: 10+ min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/total-decoding-messages1235/1)  

A top secret message containing letters from A-Z is being encoded to numbers using the following mapping:

```
'A' -> 1
'B' -> 2
...
'Z' -> 26
```

You are an FBI agent. You have to determine the total number of ways that message can be decoded, as the answer can be large return the answer modulo 10^9 + 7.

Note: An empty digit sequence is considered to have one decoding. It may be assumed that the input contains valid digits from 0 to 9 and If there are leading 0s, extra trailing 0s and two or more consecutive 0s then it is an invalid string.
 

**Your Task:** 

You don't need to read or print anything. Your task is to complete the function CountWays() which takes the string as str as input parameter and returns the total number of ways the string can be decoded modulo 10^9 + 7.



**Expected Time Complexity:** `O(N)`              
**Expected Auxiliary Space:** `O(N)` 



### Examples

**Example 1:**   
```
Input: str = "123"
Output: 3
Explanation: "123" can be decoded as "ABC"(123),
"LC"(12 3) and "AW"(1 23).
```

**Example 2:**   
```
Input: str = "90"
Output: 0
Explanation: "90" cannot be decoded as it's an invalid string and we cannot decode '0'.
```

### Constraints

+ `1 <= N <= 10000`

## Solutions

```cpp

class Solution {
	public:
    const unsigned int M = 1e9+7;
    int CountWays(string str){
        
        int n=str.size();
        if(n==0 or str[0]=='0'){
            return 0;
        }
        vector<long long>dp(n+1);
        dp[n]=1;
        if(str[n-1]>'0' and str[n-1]<='9'){
             dp[n-1]=1;
        }
        else{
            dp[n-1]=0;
        }
        for(int i=n-2;i>=0;i--){
            if(str[i]=='0'){
                dp[i]=0;
            }
            else
            if(str[i]=='1' or (str[i]=='2' and str[i+1]<='6')){
                 dp[i]=(dp[i+1]+dp[i+2])%M;
            }
            else{
                if(dp[i+1]==0){
                return 0;
                }
                dp[i]=0+dp[i+1];
            }
        }
        return dp[0];
    }
};

```

