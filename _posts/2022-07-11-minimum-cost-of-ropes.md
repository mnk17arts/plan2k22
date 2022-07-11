---
layout: post
title: Minimum Cost of ropes                
summary:
tags:
    - heap
    - priority-queue
    - queue
    - geeksforgeeks
    - cpp
    - easy
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/minimum-cost-of-ropes-1587115620/0/?track=DSASP-Heap&batchId=154)  

There are given `N` ropes of different lengths, we need to connect these ropes into one rope. The cost to connect two ropes is equal to sum of their lengths. The task is to connect the ropes with minimum cost.

**Your Task:** 
You don't need to read input or print anything. Your task isto complete the function `minCost()` which takes `2` arguments and returns the minimum cost.



**Expected Time Complexity:** `O(NLogN)`           
**Expected Auxiliary Space:** `O(N)`


### Examples

**Example 1:**   
```
Input:
n = 4
arr[] = {4, 3, 2, 6}
Output: 
29
Explanation:
For example if we are given 4
ropes of lengths 4, 3, 2 and 6. We can
connect the ropes in following ways.
1) First connect ropes of lengths 2 and 3.
Now we have three ropes of lengths 4, 6
and 5.
2) Now connect ropes of lengths 4 and 5.
Now we have two ropes of lengths 6 and 9.
3) Finally connect the two ropes and all
ropes have connected.
Total cost for connecting all ropes is 5
+ 9 + 15 = 29. This is the optimized cost
for connecting ropes. Other ways of
connecting ropes would always have same
or more cost. For example, if we connect
4 and 6 first (we get three strings of 3,
2 and 10), then connect 10 and 3 (we get
two strings of 13 and 2). Finally we
connect 13 and 2. Total cost in this way
is 10 + 13 + 15 = 38.
``` 


**Example 2:**   
```
Input:
n = 5
arr[] = {4, 2, 7, 6, 9}
Output: 
62 
Explanation:
First, connect ropes 4 and 2, which makes
the array {6,7,6,9}. Next, add ropes 6 and
6, which results in {12,7,9}. Then, add 7
and 9, which makes the array {12,16}. And
finally add these two which gives {28}.
Hence, the total cost is 6 + 12 + 16 + 
28 = 62.
```


### Constraints

+ `1 <= N <= 10^5`
+ `1 <= arr[i] <= 10^6`

## Solutions

```cpp
class Solution
{
    public:
    //Function to return the minimum cost of connecting the ropes.
    long long minCost(long long arr[], long long n) {
        // Your code here
        priority_queue<long long,vector<long long>,greater<long long>> pq(arr,arr+n);
        long long res = 0;
        while(pq.size()>1){
            long long a = pq.top(); pq.pop();
            long long b = pq.top(); pq.pop();
            a += b;
            res += a;
            pq.push(a);
        }
        return res;
    }
};
```

