---
layout: post
title: Reverse a linked list  
summary:
tags:
    - linkedlist
    - geeksforgeeks
    - cpp
    - easy
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/reverse-a-linked-list/0/?track=DSASP-LinkedList&batchId=154#)  

Given a linked list of `N` nodes. The task is to reverse this list.

**Your Task:** 
The task is to complete the function `reverseList()` with head reference as the only argument and should return new head after reversing the list. 


**Expected Time Complexity:** `O(N)` 
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
LinkedList: 1->2->3->4->5->6
Output: 6 5 4 3 2 1
Explanation: After reversing the list, 
elements are 6->5->4->3->2->1.
```

**Example 2:**   
```
Input:
LinkedList: 2->7->8->9->10
Output: 10 9 8 7 2
Explanation: After reversing the list,
elements are 10->9->8->7->2.
```


### Constraints

+ `1 <= N <= 10^4`

## Solutions

```cpp
class Solution{
    public:
    //Function to reverse a linked list.
    struct Node* reverseList(struct Node *head)
    {
        // code here
        if(head==NULL || head->next==NULL) return head;
        Node* prev = NULL, *curr = head, *next;
        while(curr!=NULL){
            next = curr->next;
            curr->next = prev;
            prev = curr;
            curr = next;
        }
        return prev;
        // return head of reversed list
    }
};
```

