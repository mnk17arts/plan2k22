---
layout: post
title: Swap Nodes in Pairs
description: 
summary: 
tags:
    - linkedlist
    - recursion
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/swap-nodes-in-pairs/)
Given a linked list, swap every two adjacent nodes and return its head. You must solve the problem without modifying the values in the list's nodes (i.e., only nodes themselves may be changed.)

### Examples

**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2020/10/03/swap_ex1.jpg">
```
Input: head = [1,2,3,4]
Output: [2,1,4,3]
```

**Example 2:**  
```
Input: head = []
Output: []
```

**Example 3:**  
```
Input: head = [1]
Output: [1]
```

### Constraints
+ The number of nodes in the list is the range `[0, 100]`.
+ `0 <= Node.val <= 100`


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
    ListNode* myList = new ListNode();
    ListNode* swapPairs(ListNode* pre,ListNode* cur){

        if(!cur || !cur->next) return cur;

        ListNode* nxt = swapPairs(cur->next,cur->next->next);
        ListNode* temp = cur;
        pre->next = temp->next;
        temp->next = nxt;
        pre->next->next = temp;
        
        return pre->next;
        
    }
    ListNode* swapPairs(ListNode* head) {

        if(!head || !head->next) return head;

        myList = swapPairs(myList,head);
        
        return myList;
    }
};

```
