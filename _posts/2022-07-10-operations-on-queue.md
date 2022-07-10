---
layout: post
title:  Operations on Queue             
summary:
tags:
    - queue
    - geeksforgeeks
    - cpp
    - easy
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/operations-on-queue/0/?track=DSASP-Queue&batchId=154)  

Given a queue of integers and Q queries. The task is to perform operations on queue according to the query. 

Queries are as:

1. `i x` : (adds element `x` in the queue from rear).

1. `r` : (Removes the front element of queue).

1. `h` : (Returns the front element).

1. `f y` : (check if the element `y` is present or not in the queue). Return "Yes" if present, else "No"


**Your Task:** 
Your task is to complete functions `enqueue()`, `dequeue()`, `front()` and `find()` which performs the operations described above in the problem description. 


**Expected Time Complexity:** `O(1)` or `enqueue()`, `dequeue()` and `front()`; `O(N)` for `find()`.     
**Expected Auxiliary Space:** `O(1)` 


### Examples

**Example 1:**   
```
Input:
Q = 4
Queries = i 3 i 4 r f 3
Output: No
Explanation: Inserting 3 and 4 . When
we return and remove 3 and then when
we find 3 , it will return NO as
output as 3 is not present in the
queue.
```


**Example 2:**   
```
Input:
Q = 6
Queries = i 2 i 4 i 3 i 5 h f 8
Output:
2
No
Explanation: Inserting 2, 4, 3, and 5
onto the queue: 2 4 3 5. h means front
So front is 2. f is find. 8 is not in
queue so No.
```


### Constraints

+ `1 <= Q <= 10^3`

## Solutions

```cpp
class Solution{
    public:
    
    //Function to push an element in queue.
    void enqueue(queue<int> &q,int x)
    {
       //Your code here
       q.push(x);
    }
     
    //Function to remove front element from queue.
    void dequeue(queue<int> &q)
    {
        //Your code here
        q.pop();
    }
    
    //Function to find the front element of queue.
    int front(queue<int> &q)
    {
        //Your code here
        return q.front();
    }
    
    //Function to find an element in the queue.
    string find(queue<int> q, int x)
    {
        //Your code here
        int n = q.size();
        for(int i=0; i<n; i++){
            int y = q.front(); q.pop();
            if(y==x) return "Yes";
        } 
        return "No";
    }
};
```

