---
layout: post
title: Remove duplicate element from sorted Linked List     
summary:
tags:
    - linkedlist
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/remove-duplicate-element-from-sorted-linked-list/0/?#)  

Given a singly linked list consisting of `N` nodes. The task is to remove duplicates (nodes with duplicate values) from the given list (if exists).
Note: Try not to use extra space. Expected time complexity is `O(N)`. The nodes are arranged in a sorted way.

**Your Task:** 
The task is to complete the function `removeDuplicates()` which should remove the duplicates from linked list and return the head of the linkedlist.


**Expected Time Complexity:** `O(N)`    
**Expected Auxiliary Space:** `O(1)`

### Examples

**Example 1:**   
```
Input:
LinkedList: 2->2->4->5
Output: 2 4 5
Explanation: In the given linked list 
2 ->2 -> 4-> 5, only 2 occurs more 
than 1 time.
```

**Example 2:**   
```
Input:
LinkedList: 2->2->2->2->2
Output: 2
Explanation: In the given linked list 
2 ->2 ->2 ->2 ->2, 2 is the only element
and is repeated 5 times.
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

    //Function to remove duplicates from sorted linked list.
    Node *removeDuplicates(Node *head)
    {
    // your code goes here
        Node *res = head;
        while(head!=NULL && head->next!=NULL){
            if(head->data == head->next->data)
                head->next = head->next->next;
            else head = head->next; 
        }
        return res;
    
    }
};
```

