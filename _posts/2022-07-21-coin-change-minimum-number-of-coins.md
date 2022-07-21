---
layout: post
title: Coin Change - Minimum number of coins                      
summary:
tags:
    - dynamic-programming
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/coin-change-minimum-number-of-coins/0/?track=DSASP-DP&batchId=154#)  

You are given an amount denoted by value. You are also given an array of coins. The array contains the
denominations of the give coins. You need to find the minimum number of coins to make the change for value using the coins of given denominations. Also, keep in mind that you have infinite supply of the coins.

**Your Task:** 

You only need to complete the function `minimumNumberOfCoins()` that take array of `coins`, size of array, and `value` as parameters. You need to return the minimum number of coins required. If it is not possible to make the exact value out of the given coin denominations, return `-1` ("Not Possible" will be printed by the driver's code in this case).


**Expected Time Complexity:** `O(number of coins * value)`              
**Expected Auxiliary Space:** `O(value)`


### Examples

**Example 1:**   
```
Input:
value = 5
numberOfCoins = 3
coins[] = {3,6,3}
Output: Not Possible
Explanation:We need to make the change for
value = 5 The denominations are {3,6,3}
It is certain that we cannot make 5 using
any of these coins.
```

**Example 2:**   
```
Input:
value = 10
numberOfCoins = 4
coins[] = {2 5 3 6}
Output: 2
Explanation:We need to make the change for
value = 10 The denominations are {2,5,3,6}
We can use two 5 coins to make 10. So
minimum coins are 2.
```

### Constraints

+ `1 <= value <= 10^3`
+ `1 <= numberOfCoins <= 10^3`
+ `1 <= coins[i] <= 10^3`


## Solutions

```cpp
class Solution
{
    public:
    //Function to find the minimum number of coins to make the change 
    //for value using the coins of given denominations.
    long long minimumNumberOfCoins(int coins[],int numberOfCoins,int value)
    {
        // your code here
        long long dp[value+1];
        dp[0]=0;
        for(int i=1;i<value+1;i++){
            dp[i]=INT_MAX;
            for(int j=0;j<numberOfCoins;j++){
                if(coins[j]<=i)
                    dp[i] = min(dp[i],dp[i-coins[j]]+1);
            }
        }
        return dp[value]==INT_MAX ? -1 : dp[value];
    }
};
```

