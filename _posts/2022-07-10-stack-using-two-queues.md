---
layout: post
title:  Stack using two queues              
summary:
tags:
    - queue
    - stack
    - geeksforgeeks
    - cpp
    - easy
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/stack-using-two-queues/0/?track=DSASP-Queue&batchId=154#)  

Implement a Stack using two queues `q1` and `q2`


**Your Task:** 
Since this is a function problem, you don't need to take inputs. You are required to complete the two methods `push()` which takes an integer '`x`' as input denoting the element to be pushed into the stack and `pop()` which returns the integer poped out from the stack(`-1` if the stack is empty).


**Expected Time Complexity:** `O(1)`   for `push()` and `O(N)` for `pop()` or `O(N)` for `push()` and `O(1)` for `pop()`         
**Expected Auxiliary Space:** `O(1)` 


### Examples

**Example 1:**   
```
Input:
push(2)
push(3)
pop()
push(4)
pop()
Output: 3 4
Explanation:
push(2) the stack will be {2}
push(3) the stack will be {2 3}
pop()   poped element will be 3 the 
        stack will be {2}
push(4) the stack will be {2 4}
pop()   poped element will be 4  
```


**Example 2:**   
```
Input:
push(2)
pop()
pop()
push(3)
Output: 2 -1

```


### Constraints

+ `1 <= N <= 100`
+ `1 <= x <= 100`

## Solutions

```cpp
//Function to push an element into stack using two queues.
void QueueStack :: push(int x)
{
        // Your Code
    q1.push(x);
    while(!q2.empty()) { q1.push(q2.front()); q2.pop(); }
    while(!q1.empty()) { q2.push(q1.front()); q1.pop(); }
    
}

//Function to pop an element from stack using two queues. 
int QueueStack :: pop()
{
    // Your Code   
    int res = -1;
    if(!q2.empty()) { res = q2.front(); q2.pop(); }
    return res;
}
```

