---
layout: post
title: Implement Queue using Linked List              
summary:
tags:
    - queue
    - geeksforgeeks
    - cpp
    - easy
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/implement-queue-using-linked-list/0/?track=DSASP-Queue&batchId=154#)  

Implement a Queue using Linked List. 
A Query Q is of 2 Types
1. `1 x`   (a query of this type means  pushing 'x' into the queue)
1. `2`     (a query of this type means to pop an element from the queue and print the poped elemen


**Your Task:** 
Complete the function `push()` which takes an integer as input parameter and `pop()` which will remove and return an element(`-1` if queue is empty).


**Expected Time Complexity:** `O(1)`       
**Expected Auxiliary Space:** `O(1)` 


### Examples

**Example 1:**   
```
Input:
Q = 4
Queries = 1 2 2 2 1 3 
Output: 2 -1
Explanation: In the second testcase 
1 2 the queue will be {2}
2   poped element will be {2} then
    the queue will be empty. 
2   the queue is empty and hence -1
1 3 the queue will be {3}.
```


**Example 2:**   
```
Input:
Q = 5
Queries = 1 2 1 3 2 1 4 2
Output: 2 3
Explanation: n the first testcase
1 2 the queue will be {2}
1 3 the queue will be {2 3}
2   poped element will be 2 the
    queue will be {3}
1 4 the queue will be {3 4}
2   poped element will be 3.

```


### Constraints

+ `1 <= Q <= 100`
+ `1 <= x <= 100`

## Solutions

```cpp
//Function to push an element into the queue.
void MyQueue:: push(int x)
{
        // Your Code
    QueueNode* temp = new QueueNode(x);
    if(!front) { front=rear=temp; return; }
    rear->next = temp;
    rear = rear->next;
    
}

//Function to pop front element from the queue.
int MyQueue :: pop()
{
        // Your Code 
    int ele = -1;
    if(front) {
        ele = front->data;     
        if(!front->next) 
            front = rear = NULL;  
        else
            front = front->next;
    }
    return ele;
    
}
```

