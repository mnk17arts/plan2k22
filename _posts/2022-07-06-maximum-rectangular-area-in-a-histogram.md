---
layout: post
title: Maximum Rectangular Area in a Histogram      
summary:
tags:
    - stack
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/maximum-rectangular-area-in-a-histogram-1587115620/0/?track=DSASP-Stack&batchId=154#?)  

Find the largest rectangular area possible in a given histogram where the largest rectangle can be made of a number of contiguous bars. For simplicity, assume that all bars have the same width and the width is 1 unit, there will be `N` bars height of each bar will be given by the array arr.


**Your Task:** 
The task is to complete the function `getMaxArea()` which takes the array `arr[]` and its size `N` as inputs and finds the largest rectangular area possible and returns the answer.

**Expected Time Complexity:** `O(N)` 
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input:
N = 7
arr[] = {6,2,5,4,5,1,6}
Output: 12
Explanation: 
```
<img src="http://d1hyf4ir1gqw6c.cloudfront.net/wp-content/uploads/histogram1.png">

**Example 2:**   
```
Input:
N = 8
arr[] = {7 2 8 9 1 3 6 5}
Output: 16
Explanation: Maximum size of the histogram 
will be 8  and there will be 2 consecutive 
histogram. And hence the area of the 
histogram will be 8x2 = 16.
```


### Constraints

+ `1 <= N <= 10^6`
+ `1 <= Arri <= 10^12`

## Solutions

```cpp
class Solution{
    public:
    //Function to find largest rectangular area possible in a given histogram.
    long long getMaxArea(long long arr[], int n)
    {
        // Your code here
        long long res = 0;
        stack<int> s;
        for(int i=0; i<=n; i++){
            long long cur_height = (i==n) ? 0 : arr[i];
            while(!s.empty() && arr[s.top()] >= cur_height){
                long long h = arr[s.top()]; s.pop();
                int w = s.empty() ? i : i - s.top() - 1;
                res = max(res, w*h);
            }
            s.push(i);
        }
        return res;
    }
};
```

