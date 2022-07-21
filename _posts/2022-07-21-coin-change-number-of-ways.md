---
layout: post
title: Coin Change - Number of ways                      
summary:
tags:
    - dynamic-programming
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/coin-change-number-of-ways/0/?track=DSASP-DP&batchId=154#)  

You have an infinite supply of coins, each having some value. Find out the number of ways to use the coins to sum-up to a certain required value.

**Your Task:** 

This is a function problem where you've to complete the funcion `numberOfWays ()`. You are given an amount denoted by `value`. You are also given an array of coins. The array contains the denominations of the given coins. You need to return the number of ways you can make the change for value using the coins of given denominations. Also, keep in mind that you have an infinite supply of coins.

Note:  Try not to editing the part of the code provided to you in the function. Just complete the function as it has been described.


**Expected Time Complexity:** `O(number of coins * value)`              
**Expected Auxiliary Space:** `O(value)`


### Examples

**Example 1:**   
```
Input:
value = 4
numberOfCoins = 3
coins[] = {1,2,3}
Output: 4
Explanation: We need to make the change
for value = 4. The denominations are
{1,2,3} Change for 4 can be made:
1+1+1+1
1+1+2
1+3
2+2
So, as it is evident, we can do this in
4 ways.
```

**Example 2:**   
```
Input:
value = 10
numberOfCoins = 4
coins[] = {2,5,3,6}
Output: 5
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
    //Function to find out the number of ways to use the coins to
    //sum up to a certain required value.
    long long numberOfWays(int coins[],int numberOfCoins,int value)
    {
        long long dp[value+1][numberOfCoins+1];
        for(int i=0;i<=numberOfCoins;i++) dp[0][i] = 1;
        for(int i=1;i<=value;i++) dp[i][0] = 0;
        for(int i=1;i<value+1;i++){
            for(int j=1;j<numberOfCoins+1;j++){
                if(coins[j-1]<=i)
                    dp[i][j] = dp[i][j-1] + dp[i-coins[j-1]][j];
                else dp[i][j] = dp[i][j-1];
            }
        }
        return dp[value][numberOfCoins];
    }
};
```

