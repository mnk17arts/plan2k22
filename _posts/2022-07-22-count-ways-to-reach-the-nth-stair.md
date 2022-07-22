---
layout: post
title: Count ways to reach the n'th stair                       
summary:
tags:
    - dynamic-programming
    - geeksforgeeks
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/count-ways-to-reach-the-nth-stair-1587115620/0/?track=DSASP-DP&batchId=154#)  

There are `n` stairs, a person standing at the bottom wants to reach the top. The person can climb either `1` stair or `2` stairs at a time. Count the number of ways, the person can reach the top (order does matter).

**Your Task:** 

Complete the function `countWays()` which takes the top stair number `m` as input parameters and returns the answer % `10^9+7`.


**Expected Time Complexity:** `O(n)`              
**Expected Auxiliary Space:** `O(1)`


### Examples

**Example 1:**   
```
Input:
n = 4
Output: 5
Explanation:
You can reach 4th stair in 5 ways. 
Way 1: Climb 2 stairs at a time. 
Way 2: Climb 1 stair at a time.
Way 3: Climb 2 stairs, then 1 stair
and then 1 stair.
Way 4: Climb 1 stair, then 2 stairs
then 1 stair.
Way 5: Climb 1 stair, then 1 stair and
then 2 stairs.
```

**Example 2:**   
```
Input:
n = 10
Output: 89 
Explanation: 
There are 89 ways to reach the 10th stair.
```

### Constraints

+ `1 <= N <= 10^4`


## Solutions

```cpp
class Solution
{
    public:
    //Function to count number of ways to reach the nth stair.
    int countWays(int n)
    {
        // your code here
        if(n<3) return n;
        int pre_pre = 1;
        int pre = 2;
        int mod = 1e9+7;
        for(int i=2;i<n;i++){
            int temp = pre + pre_pre;
            pre_pre = pre;
            pre = temp%mod;
        }
        return pre;
    }
};
```

