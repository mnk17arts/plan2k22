---
layout: post
title: Nth node from end of linked list      
summary:
tags:
    - linkedlist
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/nth-node-from-end-of-linked-list/0/?#)  

Given a linked list consisting of `L` nodes and given a number `N`. The task is to find the `N`th node from the end of the linked list.

**Your Task:** 
The task is to complete the function `getNthFromLast()` which takes two arguments: reference to `head` and `N` and you need to return `N`th from the end or `-1` in case node doesn't exist.  


**Expected Time Complexity:** `O(N)`    
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
N = 2
LinkedList: 1->2->3->4->5->6->7->8->9
Output: 8
Explanation: In the first example, there
are 9 nodes in linked list and we need
to find 2nd node from end. 2nd node
from end os 8.  
```

**Example 2:**   
```
Input:
N = 5
LinkedList: 10->5->100->5
Output: -1
Explanation: In the second example, there
are 4 nodes in the linked list and we
need to find 5th from the end. Since 'n'
is more than the number of nodes in the
linked list, the output is -1.
```

### Constraints

+ `1 <= L <= 10^6`
+ `1 <= N <= 10^6`

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

    //Function to find the data of nth node from the end of a linked list.
    int getNthFromLast(Node *head, int n)
    {
        // Your code here
        Node* front = head;
        for(int i=0; i<n; i++){
            if(front==NULL) return -1;
            front = front->next;
        }
        Node* back = head;
        while(front!=NULL){
            front = front->next;
            back = back->next;
        }
        return back->data;
    }
};
```

