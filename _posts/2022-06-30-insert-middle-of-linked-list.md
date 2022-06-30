---
layout: post
title: Insert in Middle of Linked List    
summary:
tags:
    - linkedlist
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/insert-in-middle-of-linked-list/0/?#)  

Given a linked list of size `N` and a `key`. The task is to insert the key in the middle of the linked list.

**Your Task:** 
The task is to complete the function `insertInMiddle()` which takes head reference and element to be inserted as the arguments. The printing is done automatically by the driver code.


**Expected Time Complexity:** `O(N)`    
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
LinkedList = 1->2->4
key = 3
Output: 1 2 3 4
Explanation: The new element is inserted
after the current middle element in the
linked list.
```

**Example 2:**   
```
Input:
LinkedList = 10->20->40->50
key = 30
Output: 10 20 30 40 50
Explanation: The new element is inserted
after the current middle element in the
linked list and Hence, the output is
10 20 30 40 50.
```

### Constraints

+ `1 <= N <= 10^4`

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

    //Function to insert a node in the middle of the linked list.
    Node* insertInMiddle(Node* head, int x)
    {
        // Code here
        Node* fast = head;
        Node* slow = head;
        while(fast->next!=NULL && fast->next->next!=NULL){
            fast=fast->next->next;
            slow=slow->next;
        }
        Node* temp = new Node(x);
        temp->next = slow->next;
        slow->next = temp;
        return head;
    }
};
```

