---
layout: post
title: Count ways to N'th Stair(Order does not matter)                       
summary:
tags:
    - dynamic-programming
    - geeksforgeeks
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/count-ways-to-nth-stairorder-does-not-matter1322/0/?track=DSASP-DP&batchId=154#)  

There are `N` stairs, and a person standing at the bottom wants to reach the top. The person can climb either `1` stair or `2` stairs at a time. Count the number of ways, the person can reach the top (order does not matter).
Note: Order does not matter means for `n=4 {1 2 1},{2 1 1},{1 1 2}` are considered same.

**Your Task:** 

Your task is to complete the function `countWays()` which takes single argument(`N`) and returns the answer.


**Expected Time Complexity:** `O(N)`              
**Expected Auxiliary Space:** `O(N)`


### Examples

**Example 1:**   
```
Input:
N = 4
Output: 3
Explanation: You can reach 4th stair in
3 ways.
3 possible ways are:
1, 1, 1, 1
1, 1, 2
2, 2
```

**Example 2:**   
```
Input:
N = 5
Output: 3
Explanation:
You may reach the 5th stair in 3 ways.
The 3 possible ways are:
1, 1, 1, 1, 1
1, 1, 1, 2
1, 2, 2
```

### Constraints

+ `1 <= N <= 10^6`


## Solutions

```cpp
class Solution
{
    public:
    //Function to count number of ways to reach the nth stair 
    //when order does not matter.
    long long countWays(int m)
    {
        // your code here
        long long dp[m+1][3];
        dp[0][0]=dp[0][1]=dp[0][2]=1;
        for(int i=1;i<=m;i++){
            dp[i][0] = dp[i][1] = 0;
            if(i>=1) dp[i][1] += dp[i-1][1];
            dp[i][2] = dp[i][1];
            if(i>=2) dp[i][2] += dp[i-2][2];
        }
        return dp[m][2];
    }
};
```

