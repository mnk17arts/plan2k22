---
layout: post
title:  Optimal Strategy For A Game                        
summary:
tags:
    - dynamic-programming
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/optimal-strategy-for-a-game-1587115620/0/?track=DSASP-DP&batchId=154)  

You are given an array `A` of size `N`. The array contains integers and is of even length. The elements of the array represent `N` coin of values `V1, V2, ....Vn`. You play against an opponent in an alternating way.

In each turn, a player selects either the first or last coin from the row, removes it from the row permanently, and receives the value of the coin.

You need to determine the maximum possible amount of money you can win if you go first.
Note: Both the players are playing optimally.

**Your Task:** 

Complete the function `maximumAmount()` which takes an array `arr[]` (represent values of `N` coins) and `N` as number of coins as a parameter and returns the maximum possible amount of money you can win if you go first.




**Expected Time Complexity:** `O(N*N)`                
**Expected Auxiliary Space:** `O(N*N)` 


### Examples

**Example 1:**   
```
Input:
N = 4
A[] = {5,3,7,10}
Output: 15
Explanation: The user collects maximum
value as 15(10 + 5)
```

**Example 2:**   
```
Input:
N = 4
A[] = {8,15,3,7}
Output: 22
Explanation: The user collects maximum
value as 22(7 + 15)
```

### Constraints

+ `2 <= N <= 1000`
+ `1 <= A[i] <= 10^6`


## Solutions

```cpp
class Solution
{
    public:
    long long maximumAmount(int arr[], int n){
        // Your code here
        long long dp[n][n];
        for(int i=0;i<n-1;i++)
            dp[i][i+1] = max(arr[i],arr[i+1]);
        for(int gap=3;gap<n;gap+=2)
            for(int i=0;i<n-gap;i++){
                int j=gap+i;
                dp[i][j] = max (
                    arr[i] + min(dp[i+1][j-1], dp[i+2][j]),
                    arr[j] + min(dp[i+1][j-1], dp[i][j-2])
                    );
            }
        return dp[0][n-1];
    }
};
```

