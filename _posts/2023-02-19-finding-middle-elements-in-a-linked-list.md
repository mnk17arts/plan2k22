---
layout: post
title: Finding middle element in a linked list
summary:
tags:
  - geeksforgeeks
  - array
  - binary-search
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/finding-middle-element-in-a-linked-list/1)

Given a singly linked list of N nodes.
The task is to find the middle of the linked list. For example, if the linked list is 1->2->3->4->5, then the middle node of the list is 3.
If there are two middle nodes(in case, when N is even), print the second middle element.
For example, if the linked list given is 1->2->3->4->5->6, then the middle node of the list is 4

**Your Task:**

The task is to complete the function getMiddle() which takes a head reference as the only argument and should return the data at the middle node of the linked list.


**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**

```
Input:
LinkedList: 1->2->3->4->5
Output: 3 
Explanation: 
Middle of linked list is 3.
```

**Example 2:**

```
Input:
LinkedList: 2->4->6->7->5->1
Output: 7 
Explanation: 
Middle of linked list is 7.
```

### Constraints

- `1 ≤ N ≤ 5000`

## Solutions

```cpp

/* Link list Node 
struct Node {
    int data;
    Node* next;
    
    Node(int x){
        data = x;
        next = NULL;
    }
    
}; */

class Solution{
    public:
    /* Should return data of middle node. If linked list is empty, then  -1*/
    int getMiddle(Node *head)
    {
        // Your code here
        Node *slow = head, *fast = head;
        while(fast && fast->next) {
            slow = slow->next;
            fast = fast->next->next;
        }
        return slow->data;
        
    }
};

```
