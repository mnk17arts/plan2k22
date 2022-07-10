---
layout: post
title: Queue Reversal              
summary:
tags:
    - queue
    - stack
    - geeksforgeeks
    - cpp
    - easy
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/queue-reversal/0/?track=DSASP-Queue&batchId=154)  

Given a Queue `Q` containing `N` elements. The task is to reverse the Queue. Your task is to complete the function `rev()`, that reverses the `N` elements of the queue.


**Your Task:** 
You only need to complete the function rev that takes a queue as parameter and returns the reversed queue. The printing is done automatically by the driver code.


**Expected Time Complexity:** `O(n)`       
**Expected Auxiliary Space:** `O(n)` 


### Examples

**Example 1:**   
```
Input:
6
4 3 1 10 2 6

Output: 
6 2 10 1 3 4

Explanation: 
After reversing the given
elements of the queue , the resultant
queue will be 6 2 10 1 3 4.
```


**Example 2:**   
```
Input:
4
4 3 2 1 

Output: 
1 2 3 4

Explanation: 
After reversing the given
elements of the queue , the resultant
queue will be 1 2 3 4.

```


### Constraints

+ `1 <= N <= 100`
+ `1 <= x <= 100`

## Solutions

```cpp
queue<int> rev(queue<int> q)
{
    // add code here.
    stack<int> s;
    while(!q.empty()){
        s.push(q.front());
        q.pop();
    }
    while(!s.empty()){
        q.push(s.top());
        s.pop();
    }
    return q;
}
```

