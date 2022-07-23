---
layout: post
title: Longest Increasing Subsequence                       
summary:
tags:
    - dynamic-programming
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/longest-increasing-subsequence-1587115620/0/?track=DSASP-DP&batchId=154)  

Given an array of integers, find the length of the longest (strictly) increasing subsequence from the given array. 

**Your Task:** 

Complete the function `longestSubsequence()` which takes the input array and its size as input parameters and returns the length of the longest increasing subsequence.


**Expected Time Complexity:** `O(N*logN)`                
**Expected Auxiliary Space:** `O(N)`


### Examples

**Example 1:**   
```
Input:
N = 16
A[]={0,8,4,12,2,10,6,14,1,9,5
     13,3,11,7,15}
Output: 6
Explanation:Longest increasing subsequence
0 2 6 9 13 15, which has length 6
```

**Example 2:**   
```
Input:
N = 6
A[] = {5,8,3,7,9,1}
Output: 3
Explanation:Longest increasing subsequence
5 7 9, with length 3
```

### Constraints

+ `1 <= N <= 10^5`
+ `0 <= A[i] <= 10^6`


## Solutions

```cpp
class Solution
{
    public:
    int ceil_(int tail[],int len,int key){
        int l=0,r=len-1;
        while(l<r){
            int mid = l + (r-l)/2;
            if(tail[mid]>=key) r = mid;
            else l = mid+1;
        }
        return r;
    }
    //Function to find length of longest increasing subsequence.
    int longestSubsequence(int n, int a[])  {
        // your code here
        int tail[n], len=0;
        tail[len++] = a[0];
        for(int i=1;i<n;i++)
            if(tail[len-1]<a[i]) tail[len++]=a[i];
            else tail[ceil_(tail,len,a[i])] = a[i];
        return len;
    }
};
```

