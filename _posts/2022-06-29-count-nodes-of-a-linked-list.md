---
layout: post
title: Count nodes of linked list    
summary:
tags:
    - linkedlist
    - geeksforgeeks
    - cpp
    - easy
minute: 2 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/count-nodes-of-linked-list/0/?)  

Given a singly linked list. The task is to find the length of the linked list, where length is defined as the number of nodes in the linked list.

**Your Task:** 
Your task is to complete the given function `getCount()`, which takes a head reference as an argument and should return the length of the linked list. 


**Expected Time Complexity:** `O(N)` 
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
LinkedList: 1->2->3->4->5
Output: 5
Explanation: Count of nodes in the 
linked list is 5, which is its length.
```

**Example 2:**   
```
Input:
LinkedList: 2->4->6->7->5->1->0
Output: 7
Explanation: Count of nodes in the
linked list is 7. Hence, the output
is 7.
```

### Constraints

+ `1 <= N <= 10^5`
+ `1 <= value <= 10^3`

## Solutions

```cpp
class Solution{
    public:
    //Function to count nodes of a linked list.
    int getCount(struct Node* head){
    
        //Code here
        int res = 0;
        while(head!=NULL){ res++; head=head->next;}
        return res;
    
    }
};
```

