---
layout: post
title: Add Two Numbers II
description: 
summary: 
tags:
    - linkedlist
    - leetcode
    - cpp
    - medium
minute: 5 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/add-two-numbers-ii/)
You are given two **non-empty** linked lists representing two non-negative integers. The most significant digit comes first and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

### Examples
**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2021/04/09/sumii-linked-list.jpg" height="250">
```
Input: l1 = [7,2,4,3], l2 = [5,6,4]
Output: [7,8,0,7]
```

**Example 2:**  
```
Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [8,0,7]
```

**Example 3:**  
```
Input: l1 = [0], l2 = [0]
Output: [0]
```

### Constraints
+ The number of nodes in each linked list is in the range `[1, 100]`
+ `0 <= Node.val <= 9`
+ It is guaranteed that the list represents a number that does not have leading zeros.

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
    ListNode* reverseRecursive(ListNode* head) {
    if (!head || !(head -> next)) {
        return head;
    }
    ListNode* node = reverseRecursive(head -> next);
    head -> next -> next = head;
    head -> next = NULL;
    return node;
    }
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        l1 = reverseRecursive(l1);
        l2 = reverseRecursive(l2);
        
ListNode* up = new ListNode() ;
        ListNode* down = new ListNode();
      
        down->val = -1;
        down->next = NULL;
        up = down;
        int carry = 0;
      
        while(l1 != NULL || l2 != NULL){
          
            int a=0,b=0,s=0,v=0;
          
            if( l1!=NULL ) a = l1->val;
            if( l2!=NULL ) b = l2->val;
          
            s = a + b + carry;
            v = s%10;
          
            ListNode* temp = new ListNode();   
            temp->val = v;
          
            carry = s/10;
          
            down->next = temp;
            down = down->next;
          
            if(l1!=NULL && l1->next!=NULL)
                l1 = l1 -> next;
            else
                l1 = NULL;
            if(l2!=NULL && l2->next!=NULL)
                l2 = l2 -> next;
            else 
                l2 = NULL;
        }
      
        if(carry){
            ListNode* temp = new ListNode(); ;
            temp->val = carry;
            down->next = temp;
        }
        up = reverseRecursive(up->next);
        return up;
    }
};
```
