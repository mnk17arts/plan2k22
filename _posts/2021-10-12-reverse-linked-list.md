---
layout: post
title: Reverse Linked List
description: 
summary: 
tags:
    - linkedlist
    - leetcode
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/reverse-linked-list/)
Given the `head` of a singly linked list, reverse the list, and return *the reversed list.*

### Examples

**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2021/02/19/rev1ex1.jpg">
```
Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]
```

**Example 2:**  
<img src="https://assets.leetcode.com/uploads/2021/02/19/rev1ex2.jpg">
```
Input: head = [1,2]
Output: [2,1]
```

**Example 3:**  
```
Input: head = []
Output: []
```

### Constraints
+ The number of nodes in the list is the range `[0, 5000]`.
+ `-5000 <= Node.val <= 5000`

**Follow up:** A linked list can be reversed either iteratively or recursively. Could you implement both?

## Solutions

#### #1
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
    ListNode* reverseList(ListNode* cn, ListNode* pn){
        if(!cn) return pn;
        ListNode* temp = reverseList(cn->next,cn);
        cn->next = pn;
        return temp;
    }
    ListNode* reverseList(ListNode* head) {
        return reverseList(head,NULL);
    }
};

```

#### #2

```cpp

class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        ListNode* curr = head;
        ListNode* prev = nullptr;
        while (curr != nullptr) {
            ListNode* next = curr->next;
            curr->next = prev;
            prev = curr;
            curr = next;
        }
        return prev;
    }
};

```
