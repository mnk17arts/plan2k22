---
layout: post
title: Coin Change
description: 
summary:
tags:
    - array
    - bfs
    - dynamic-programming
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/coin-change/)
You are given an integer array `coins` representing coins of different denominations and an integer `amount` representing a total amount of money.

Return *the fewest number of coins that you need to make up that amount*. If that amount of money cannot be made up by any combination of the coins, return `-1`.

You may assume that you have an infinite number of each kind of coin.


### Examples

**Example 1:**  
```
Input: coins = [1,2,5], amount = 11
Output: 3
Explanation: 11 = 5 + 5 + 1
```

**Example 2:**  
```
Input: coins = [2], amount = 3
Output: -1
```

**Example 3:**  
```
Input: coins = [1], amount = 0
Output: 0
```

**Example 4:**  
```
Input: coins = [1], amount = 1
Output: 1
```

**Example 5:**  
```
Input: coins = [1], amount = 2
Output: 2
```

### Constraints
+ `1 <= coins.length <= 12`
+ `1 <= coins[i] <= 2^31 - 1`
+ `0 <= amount <= 10^4`

## Solutions

```cpp
class Solution {
public:
    int coinChange(vector<int>& coins, int amount) {
      int n = coins.size();
      int m = amount;
      int dp[n+1][m+1];
      for(int j=0; j<m+1; j++) dp[0][j] = INT_MAX-1;
      for(int i=1; i<n+1; i++) dp[i][0] = 0;
      for(int i=1; i<n+1; i++){
        for(int j=1; j<m+1; j++){
          if( coins[i-1]<=j )
            dp[i][j] = min(dp[i][j-coins[i-1]]+1, dp[i-1][j]);
          else
            dp[i][j] = dp[i-1][j];
        }
      }
      return dp[n][m]==INT_MAX-1 ? -1 : dp[n][m];
    }
};
```

