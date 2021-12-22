---
layout: post
title: Reorder List
summary:
tags:
    - linkedlist
    - pointers
    - leetcode
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/reorder-list)  

You are given the head of a singly linked-list. The list can be represented as:

`L0 → L1 → … → Ln - 1 → Ln`

Reorder the list to be on the following form:

`L0 → Ln → L1 → Ln - 1 → L2 → Ln - 2 → …`

You may not modify the values in the list's nodes. Only nodes themselves may be changed.

### Examples

**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2021/03/04/reorder1linked-list.jpg">
```
Input: head = [1,2,3,4]
Output: [1,4,2,3]
```

**Example 2:**  
<img src="https://assets.leetcode.com/uploads/2021/03/09/reorder2-linked-list.jpg">
```
Input: head = [1,2,3,4,5]
Output: [1,5,2,4,3]
```

### Constraints
+ The number of nodes in the list is in the range `[1, 5 * 10^4]`.
+ `1 <= Node.val <= 1000`

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
    void reorderList(ListNode* head) {
      if(!head or !head->next or !head->next->next) return;
      
      ListNode *h,*l,*p=NULL;
      h = l = head;
      while(l->next and l->next->next){
        h = h->next;
        l = l->next->next;
      }
      if(l->next) h=h->next; 
      while(h){
        l = h->next;
        h->next = p;
        p = h;
        h = l;
      }
      h = p;
      
      while(head and h){
        l = head->next;
        p = h->next;
        head->next = h;
        h->next = l;
        head = l;
        h = p;
      }
      if (head && head->next) head->next->next = NULL;
    }
};
```

