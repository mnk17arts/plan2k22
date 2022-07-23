---
layout: post
title: Equal Sum Partition                        
summary:
tags:
    - dynamic-programming
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/subset-sum-problem2643/0/?track=DSASP-DP&batchId=154#)  

Given a set of numbers, check whether it can be partitioned into two subsets such that the sum of elements in both subsets is same or not.

**Your Task:** 

Your task is to complete the `findPartition()` function which takes an array `a[]` and `N` as input parameter and return true if the given set can be partitioned into two subsets such that the sum of elements in both subsets is equal, else return false.
Note: The output will be `YES` or `NO` depending upon the value returned by your code. The printing is done by the driver's code.


**Expected Time Complexity:** `O(N*S)`                
**Expected Auxiliary Space:** `O(S)` where `S` is the sum of the given Array


### Examples

**Example 1:**   
```
Input:
N = 4
arr[] = {1,5,11,5}
Output: YES
Explanation: There exists two subsets
such that {1, 5, 5} and {11}.
```

**Example 2:**   
```
Input:
N = 3
arr[] = {1,3,5}
Output: NO
```

### Constraints

+ `1 <= N <= 100`
+ `0 <= arr[i] <= 100`


## Solutions

```cpp
class Solution
{
    public:
    //Function to check whether a set of numbers can be partitioned into 
    //two subsets such that the sum of elements in both subsets is same.
    bool findPartition(int a[], int n)
    {
        // code here
        int sum = accumulate(a,a+n,0);
        if(sum%2) return 0;
        sum /= 2;
        bool dp[sum + 1]={0};
        dp[0]=1;
        for(int i=0;i<n;i++)
            for(int j=sum;j>0;j--){
                bool includeNot = dp[j];
                bool include = (j>=a[i]) && dp[j-a[i]];
                dp[j] = include || includeNot; 
            }
        return dp[sum];
    }
};
```

