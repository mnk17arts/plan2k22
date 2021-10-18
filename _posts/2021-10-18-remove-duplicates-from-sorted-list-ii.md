---
layout: post
title:  Remove Duplicates from Sorted List II
description: 
summary: 
tags:
    - linkedlist
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/)
Given the head of a sorted linked list, delete all duplicates such that each element appears only once. Return the linked list sorted as well.
 
### Examples   
**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2021/01/04/linkedlist1.jpg"> 
```
Input: head = [1,2,3,3,4,4,5]
Output: [1,2,5]
```

**Example 2:**  
<img src="https://assets.leetcode.com/uploads/2021/01/04/linkedlist2.jpg">
```
Input: head = [1,1,1,2,3]
Output: [2,3]
```

### Constraints
+ The number of nodes in the list is in the range `[0, 300]`.
+ `-100 <= Node.val <= 100`
+ The list is guaranteed to be sorted in ascending order.

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

    ListNode* deleteDuplicates(ListNode* head) {
        
        if(!head or !head->next) return head;

        ListNode* t = new ListNode(-501);
        t->next = head;
        head = t;
        
        while(t->next and t->next->next){
            
            if(t->next->val == t->next->next->val){
                
                ListNode* f = t->next;
                
                while(f->next and  f->val == f->next->val)
                    f = f->next;
                t->next = f->next;
                
            }
            else t = t->next;
            
        }
        return head->next;
    }
};
```

