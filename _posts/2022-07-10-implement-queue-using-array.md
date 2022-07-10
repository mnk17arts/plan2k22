---
layout: post
title:   Implement Queue using array            
summary:
tags:
    - queue
    - array
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/implement-queue-using-array/0/?track=DSASP-Queue&batchId=154#)  

Implement a Queue using an Array. Queries in the Queue are of the following type:
1. `1 x`   (a query of this type means  pushing 'x' into the queue)
2. `2`     (a query of this type means to pop element from queue and print the poped element)


**Your Task:** 
You are required to complete the two methods `push()` which take one argument an integer '`x`' to be pushed into the queue and `pop()` which returns a integer poped out from othe queue. If the queue is empty, it should return `-1` on a pop operation. 


**Expected Time Complexity:** `O(1)`      
**Expected Auxiliary Space:** `O(1)` 


### Examples

**Example 1:**   
```
Input:
Q = 5
Queries = 1 2 1 3 2 1 4 2
Output: 2 3
Explanation:
In the first test case for query 
1 2 the queue will be {2}
1 3 the queue will be {2 3}
2   poped element will be 2 the 
    queue will be {3}
1 4 the queue will be {3 4}
2   poped element will be 3 
```


**Example 2:**   
```
Input:
Q = 4
Queries = 1 3 2 2 1 4   
Output: 3 -1
Explanation:
In the second testcase for query 
1 3 the queue will be {3}
2   poped element will be 3 the
    queue will be empty
2   there is no element in the
    queue and hence -1
1 4 the queue will be {4}. 
```


### Constraints

+ `1 <= Q <= 10^5`
+ `1 <= x <= 10^5`

## Solutions

```cpp
//Function to push an element x in a queue.
void MyQueue :: push(int x)
{
    // Your Code
    arr[rear++] = x;
}

//Function to pop an element from queue and return that element.
int MyQueue :: pop()
{
    // Your Code   
    if(rear!=front) return arr[front++];
    return -1;
}
```

