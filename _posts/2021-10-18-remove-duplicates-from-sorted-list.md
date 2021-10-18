---
layout: post
title:  Remove Duplicates from Sorted List
description: 
summary: 
tags:
    - linkedlist
    - leetcode
    - cpp
    - easy
minute: 2 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)
Given the head of a sorted linked list, delete all duplicates such that each element appears only once. Return the linked list sorted as well.
 
### Examples   
**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2021/01/04/list1.jpg"> 
```
Input: head = [1,1,2]
Output: [1,2]
```

**Example 2:**  
<img src="https://assets.leetcode.com/uploads/2021/01/04/list2.jpg">
```
Input: head = [1,1,2,3,3]
Output: [1,2,3]
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
        
        if(!head) return head;
        
        ListNode *temp ;
        temp = head ;
        
        while(temp and temp->next){
            
            if(temp->val == temp->next->val)
                temp->next = temp->next->next;
            else
                temp = temp->next;
            
        }
        
        return head; 
    }
};
```

