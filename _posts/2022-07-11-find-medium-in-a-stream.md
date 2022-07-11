---
layout: post
title: Find median in a stream               
summary:
tags:
    - heap
    - priority-queue
    - queue
    - geeksforgeeks
    - cpp
    - hard
minute: 11 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/find-median-in-a-stream-1587115620/0/?track=DSASP-Heap&batchId=154)  

Given an input stream of `N` integers. The task is to insert these numbers into a new stream and find the median of the stream formed by each insertion of `X` to the new stream.

**Your Task:** 
You are required to complete the class Solution. 
It should have `2` data members to represent `2` heaps. 
It should have the following member functions:

1. `insertHeap()` which takes `x` as input and inserts it into the heap, the function should then call `balanceHeaps()` to balance the new heap.
1. `balanceHeaps()` does not take any arguments. It is supposed to balance the two heaps.
1. `getMedian()` does not take any arguments. It should return the current median of the stream.



**Expected Time Complexity:** `O(nlogn)`           
**Expected Auxiliary Space:** `O(n)`


### Examples

**Example 1:**   
```
Input:
N = 4
X[] = 5,15,1,3
Output:
5
10
5
4
Explanation:Flow in stream : 5, 15, 1, 3 
5 goes to stream --> median 5 (5) 
15 goes to stream --> median 10 (5,15) 
1 goes to stream --> median 5 (5,15,1) 
3 goes to stream --> median 4 (5,15,1 3) 
``` 


**Example 2:**   
```
Input:
N = 3
X[] = 5,10,15
Output:
5
7.5
10
Explanation:Flow in stream : 5, 10, 15
5 goes to stream --> median 5 (5) 
10 goes to stream --> median 7.5 (5,10) 
15 goes to stream --> median 10 (5,10,15) 
```


### Constraints

+ `1 <= N <= 10^6`
+ `1 <= x <= 10^6`

## Solutions

```cpp
class Solution
{
    public:
    priority_queue<int, vector<int>, greater<int>> g;
    priority_queue<int> s;
    //Function to insert heap.
    void insertHeap(int &x) {
        if(s.size()!=g.size()) g.push(x);
        else s.push(x);
        balanceHeaps();
    }
    
    //Function to balance heaps.
    void balanceHeaps() {
        
        if(g.empty()) return;
        if(s.top() > g.top()){
            int temp = s.top(); s.pop();
            s.push(g.top()); g.pop();
            g.push(temp);
        }
    }
    
    //Function to return Median.
    double getMedian()
    {
        if(s.size()!=g.size()) return s.top();
        return (s.top()+g.top())/2.0;
        
    }
};
```

