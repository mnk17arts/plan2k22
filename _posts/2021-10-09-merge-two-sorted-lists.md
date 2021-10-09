---
layout: post
title: Merge Two Sorted Lists
description: 
summary: 
tags:
    - linkedlist
    - leetcode
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/merge-two-sorted-lists/)
Merge two sorted linked lists and return it as a **sorted list**. The list should be made by splicing together the nodes of the first two lists.

### Examples
**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2020/10/03/merge_ex1.jpg" height="250">
```
Input: l1 = [1,2,4], l2 = [1,3,4]
Output: [1,1,2,3,4,4]
```

**Example 2:**  
```
Input: l1 = [], l2 = []
Output: []
```

**Example 3:**  
```
Input: l1 = [], l2 = [0]
Output: [0]
```

### Constraints
+ The number of nodes in both lists is in the range `[0, 50]`
+ `-100 <= Node.val <= 100`
+ Both `l1` and `l2` are sorted in non-decreasing order.

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
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
         if(l1 == NULL) return l2;
         if(l2 == NULL) return l1;
        
         ListNode* left = NULL, *right = NULL;
        
         if(l1->val <= l2->val){
             left = right = l1;
             l1 = l1->next;
         } 
         else{
             left = right = l2;
             l2 = l2->next;
         }
        
        while( l1!=NULL && l2!=NULL){
            if(l1->val <= l2->val){
                right->next = l1;
                right = right->next;
                l1 = l1->next;
            }else{
                right->next = l2;
                right = right->next;
                l2 = l2->next;
            }
        }
        
        if(l2 == NULL)
            right->next = l1;
        else
            right->next = l2;
        
        return left;
    }
};
```
