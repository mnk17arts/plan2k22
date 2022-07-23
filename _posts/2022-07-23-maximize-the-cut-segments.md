---
layout: post
title: Maximize The Cut Segments                        
summary:
tags:
    - dynamic-programming
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/cutted-segments1642/0/?track=DSASP-DP&batchId=154#)  

Given an integer `N` denoting the Length of a line segment. You need to cut the line segment in such a way that the cut length of a line segment each time is either `x` , `y` or `z`. Here `x`, `y`, and `z` are integers.
After performing all the cut operations, your total number of cut segments must be maximum.

**Your Task:** 

You only need to complete the function `maximizeTheCuts()` that takes `n`, `x`, `y`, `z` as parameters and returns max number cuts.


**Expected Time Complexity:** `O(N)`                
**Expected Auxiliary Space:** `O(N)`


### Examples

**Example 1:**   
```
Input:
N = 5
x = 5, y = 3, z = 2
Output: 2
Explanation: Here total length is 5, and
the cut lengths are 5, 3 and 2. We can
make two segments of lengths 3 and 2.
```

**Example 2:**   
```
Input:
N = 4
x = 2, y = 1, z = 1
Output: 4
Explanation:Total length is 4, and the cut
lengths are 2, 1 and 1.  We can make
maximum 4 segments each of length 1.
```

### Constraints

+ `1 <= N, x, y, z <= 10^4`


## Solutions

```cpp
class Solution
{
    public:
    //Function to find the maximum number of cuts.
    int maximizeTheCuts(int n, int x, int y, int z)
    {
        //Your code here
        int w[3] = {x,y,z};
        int dp[n+1][4]={0};
        for(int i=1;i<=n;i++){
            for(int j=1;j<4;j++){
                if(i>=w[j-1] && (i-w[j-1]==0 || dp[i-w[j-1]][j])) 
                    dp[i][j] = max(dp[i][j-1], 1 + dp[i-w[j-1]][j]);
                else dp[i][j] = dp[i][j-1];
            }
        }
        return dp[n][3];
    }
};
```

