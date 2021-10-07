---
layout: post
title: Remove Nth Node From End of List
description: 
summary: 
tags:
    - linkedlist
    - pointers
    - leetcode
    - cpp
    - medium
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)  
Given the `head` of a linked list, remove the `nth` node from the end of the list and return its `head`.

### Examples
**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2020/10/03/remove_ex1.jpg" height="200">  
```
Input: head = [1,2,3,4,5], n = 2
Output: [1,2,3,5]
```

**Example 2:**  
```
Input: head = [1], n = 1
Output: []
```

**Example 2:**  
```
Input: head = [1,2], n = 1
Output: [1]
```
### Constraints
+ The number of nodes in the list is `sz`.
+ `1 <= sz <= 30`
+ `0 <= Node.val <= 100`
+ `1 <= n <= sz`

**Follow up**: Could you do this in one pass?

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
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        
        int i = 1;
        
        ListNode* left = head;
        
        while( left->next != NULL){
            left = left->next;
            i++;
        }
        
        if(n>i)return NULL;
        
        if(n==i)return head->next;
        
        int j = i - n - 1 ;
        
        left = head;
        
        while(j--)left = left -> next;

        left->next = left->next->next;

        return head;
    }
};
```
