---
layout: post
title: Queue using two Stacks              
summary:
tags:
    - queue
    - stack
    - geeksforgeeks
    - cpp
    - easy
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/queue-using-two-stacks/0/?track=DSASP-Queue&batchId=154#)  

Implement a Queue using `2` stacks `s1` and `s2` .
A Query `Q` is of `2` Types
1. `1 x` (a query of this type means  pushing '`x`' into the queue)
1. `2`   (a query of this type means to pop element from queue and print the poped element)


**Your Task:** 
You are required to complete the two methods push which take one argument an integer '`x`' to be pushed into the queue and pop which returns a integer poped out from other queue(`-1` if the queue is empty). The printing is done automatically by the driver code.


**Expected Time Complexity:** `O(1)`   for `push()` and `O(N)` for `pop()` or `O(N)` for `push()` and `O(1)` for `pop()`         
**Expected Auxiliary Space:** `O(1)` 


### Examples

**Example 1:**   
```
Input:
4
1 2 2 2 1 4

Output: 
2 -1

Explanation: 
In the second testcase 
1 2 the queue will be {2}
2   poped element will be 2 and 
    then the queue will be empty
2   the queue is empty and hence -1
1 4 the queue will be {4}.
```


**Example 2:**   
```
Input:
5
1 2 1 3 2 1 4 2

Output: 
2 3

Explanation: 
In the first testcase
1 2 the queue will be {2}
1 3 the queue will be {2 3}
2   poped element will be 2 the queue 
    will be {3}
1 4 the queue will be {3 4}
2   poped element will be 3.

```


### Constraints

+ `1 <= N <= 100`
+ `1 <= x <= 100`

## Solutions

```cpp
//Function to push an element in queue by using 2 stacks.
void StackQueue :: push(int x)
{
    // Your Code
    s1.push(x);
}

//Function to pop an element from queue by using 2 stacks.
int StackQueue :: pop()
{
        // Your Code
    int ans = -1;
    while(!s1.empty()) { s2.push(s1.top()); s1.pop(); }
    if(!s2.empty()) { ans = s2.top(); s2.pop();}
    while(!s2.empty()) { s1.push(s2.top()); s2.pop(); }
    return ans;
}
```

