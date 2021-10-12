---
layout: post
title: Remove Linked List Elements
description: 
summary: 
tags:
    - linkedlist
    - recursion
    - leetcode
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/remove-linked-list-elements/)
Given the `head` of a linked list and an integer `val`, remove all the nodes of the linked list that has `Node.val == val`, and return the new head.

### Examples

**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2021/03/06/removelinked-list.jpg">
```
Input: head = [1,2,6,3,4,5,6], val = 6
Output: [1,2,3,4,5]
```

**Example 2:**  
```
Input: head = [], val = 1
Output: []
```

**Example 3:**  
```
Input: head = [7,7,7,7], val = 7
Output: []
```

### Constraints
+ The number of nodes in the list is in the range `[0, 10^4]`.
+ `1 <= Node.val <= 50`
+ `0 <= val <= 50`


## Solutions

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    void re(ListNode* head,int val){
        if(!head->next) return;
        if(head->next->val == val){
            head->next = head->next->next;
            re(head,val);
        }    
        else
            re(head->next,val);
        
    }
    ListNode* removeElements(ListNode* head, int val) {
        if(!val || !head) return head;
        ListNode* ptr = new ListNode(0,head);
        re(ptr,val);
        return ptr->next;
    }
};

```
