---
layout: post
title: Identical Linked Lists     
summary:
tags:
    - linkedlist
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/identical-linked-lists/0/?)  

Given two Singly Linked List of `N` and `M` nodes respectively. The task is to check whether two linked lists are identical or not. 
Two Linked Lists are identical when they have same data and with same arrangement too.

**Your Task:** 
The task is to complete the function `areIdentical()` which takes the head of both linked lists as arguments and returns True or False.


**Expected Time Complexity:** `O(N)`    
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
LinkedList1: 1->2->3->4->5->6
LinkedList2: 99->59->42->20
Output: Not identical 
```

**Example 2:**   
```
Input:
LinkedList1: 1->2->3->4->5
LinkedList2: 1->2->3->4->5
Output: Identical
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

    //Function to check whether two linked lists are identical or not. 
    bool areIdentical(struct Node *head1, struct Node *head2)
    {
        // Code here
        Node* t1 = head1;
        Node* t2 = head2;
        while(t1!=NULL && t2!=NULL){
            if(t1->data!=t2->data) return false;
            t1 = t1->next;
            t2 = t2->next;
        }
        if(t1!=NULL || t2!=NULL) return false;
        return true;
    }
};
```

