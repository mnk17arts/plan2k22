---
layout: post
title: Stickler Thief                          
summary:
tags:
    - dynamic-programming
    - array
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
--- 

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/stickler-theif-1587115621/0/?track=DSASP-DP&batchId=154#)  

Stickler the thief wants to loot money from a society having n houses in a single line. He is a weird person and follows a certain rule when looting the houses. According to the rule, he will never loot two consecutive houses. At the same time, he wants to maximize the amount he loots. The thief knows which house has what amount of money but is unable to come up with an optimal looting strategy. He asks for your help to find the maximum money he can get if he strictly follows the rule. Each house has `a[i]` amount of money present in it.



**Your Task:** 

Complete the `functionFindMaxSum()` which takes an array `arr[]` and `n` as input which returns the maximum money he can get following the rules




**Expected Time Complexity:** `O(N)`                
**Expected Auxiliary Space:** `O(N)` 


### Examples

**Example 1:**   
```
Input:
n = 6
a[] = {5,5,10,100,10,5}
Output: 110
Explanation: 5+100+5=110
```

**Example 2:**   
```
Input:
n = 3
a[] = {1,2,3}
Output: 4
Explanation: 1+3=4
```

### Constraints

+ `1 <= N <= 10^4`
+ `1 <= a[i] <= 10^4`


## Solutions

```cpp
class Solution
{
    public:
    //Function to find the maximum money the thief can get.
    int FindMaxSum(int arr[], int n)
    {
        // Your code here
        if(n==1) return arr[0];
        if(n==2) return max(arr[0],arr[1]);
        int dp1 = arr[0],
            dp2 = max(arr[0],arr[1]);
        for(int i=2;i<n;i++){
            int temp = max(dp2,dp1+arr[i]);
            dp1 = dp2;
            dp2 = temp;
        }
        return dp2;
    }
};
```

