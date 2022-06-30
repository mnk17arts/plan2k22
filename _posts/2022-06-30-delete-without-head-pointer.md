---
layout: post
title: Delete without head pointer     
summary:
tags:
    - linkedlist
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/delete-without-head-pointer/0/?track=DSASP-LinkedList&batchId=154#)  

You are given a pointer/ reference to the node which is to be deleted from the linked list of `N` nodes. The task is to delete the node. Pointer/ reference to head node is not given. 
Note: No head reference is given to you. It is guaranteed that the node to be deleted is not a tail node in the linked list.

**Your Task:** 
You only need to complete the function `deleteNode` that takes reference to the node that needs to be deleted. The printing is done automatically by the driver code.


**Expected Time Complexity:** `O(1)`    
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
N = 2
value[] = {1,2}
node = 1
Output: 2
Explanation: After deleting 1 from the
linked list, we have remaining nodes
as 2.
```

**Example 2:**   
```
Input:
N = 4
value[] = {10,20,4,30}
node = 20
Output: 10 4 30
Explanation: After deleting 20 from
the linked list, we have remaining
nodes as 10, 4 and 30.
```

### Constraints

+ `1 <= N <= 10^3`

## Solutions

```cpp
class Solution{
    public:
    /*
    struct Node {
    int data;
    struct Node *next;
    Node(int x) {
        data = x;
        next = NULL;
    }
    };
    */

    //Function to delete a node without any reference to head pointer.
    void deleteNode(Node *del)
    {
       // Your code here
       swap(del->data,del->next->data);
       Node* temp = del->next;
       del->next = del->next->next;
       delete temp;
    }
};
```

