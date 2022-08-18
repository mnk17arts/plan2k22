---
layout: post
title: Longest Sub-Array with Sum K                  
summary:
tags:
    - array
    - hash
    - map
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/longest-sub-array-with-sum-k0809/1)  

Given an array containing N integers and an integer K., Your task is to find the length of the longest Sub-Array with the sum of the elements equal to the given value K.

**Your Task:** 
This is a function problem. The input is already taken care of by the driver code. You only need to complete the function smallestSubsegment() that takes an array (A), sizeOfArray (n),  sum (K)and returns the required length of the longest Sub-Array. The driver code takes care of the printing.




**Expected Time Complexity:** `O(N^2)`           
**Expected Auxiliary Space:** `O(N^2)`


### Examples

**Example 1:**   
```
Input :
A[] = {10, 5, 2, 7, 1, 9}
K = 15
Output : 4
Explanation:
The sub-array is {5, 2, 7, 1}.
```

**Example 2:**   
```
Input : 
A[] = {-1, 2, 3}
K = 6
Output : 0
Explanation: 
There is no such sub-array with sum 6.
```

### Constraints

+ `1 <= N <= 10^5`
+ `-10^5<=A[i], K<=10^5`

## Solutions

```cpp
class Solution
{
    public:
    int lenOfLongSubarr(int A[],  int N, int K) 
    { 
        // Complete the function
        int res = 0,sum=0;
        unordered_map<int,int> mp;
        for(int i=0;i<N;i++){
            sum += A[i];
            if(mp.find(sum)==mp.end())
                mp[sum]=i;
            if(sum==K) res = max(res, i+1);
            if(mp.find(sum-K)!=mp.end()){
                res = max(res, i-mp[sum-K]);
            }
        }
        return res;
    }
};
```

