---
layout: post
title: Dequeue Traversal              
summary:
tags:
    - deque
    - geeksforgeeks
    - cpp
    - easy
minute: 2 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/dequeue-traversal/0/?track=DSASP-Deque&batchId=154)  

Given a Deque `Deq` containing `N` elements, the task is to traverse the `Deq` and print the elements of it. 


**Your Task:** 
You don't have to worry about the input. You just have to complete the function `printDequeue()` which takes a dequeue as an input parameter and prints all elements of it.
Note: For multiple test cases, the output needs to be printed on different lines.


**Expected Time Complexity:** `O(N)`            
**Expected Auxiliary Space:** `O(1)` 


### Examples

**Example 1:**   
```
Input: 
5
1 2 3 4 5

Output: 
1 2 3 4 5

Explanation: 
Dqe will look like 
{1, 2, 3, 4, 5}. 
```


**Example 2:**   
```
Input:
1
1

Output: 
1

Explanation: 
Dqe will look like {1}.

```


### Constraints

+ `1 <= N <= 10^5`

## Solutions

```cpp
//Function to traverse the Deque and print the elements of it.
void printDeque(deque<int> Deq)
{
    // your code here
    for(auto i: Deq) cout << i << " ";
    cout<<endl;
} 
```

