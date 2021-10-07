---
layout: post
title: Middle of the Linked List
description: 
summary: 
tags:
    - linked-list
    - pointer
    - leetcode
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/middle-of-the-linked-list/)
Given the `head` of a singly linked list, return *the middle node of the linked list.*

If there are two middle nodes, return the second middle node.

### Examples
**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2021/07/23/lc-midlist1.jpg" width="300">  
```
Input: head = [1,2,3,4,5]
Output: [3,4,5]
Explanation: The middle node of the list is node 3.
```

**Example 2:**  
<img src="https://assets.leetcode.com/uploads/2021/07/23/lc-midlist2.jpg" width="300">  
```
Input: head = [1,2,3,4,5,6]
Output: [4,5,6]
Explanation: Since the list has two middle nodes with values 3 and 4, we return the second one.
```

### Constraints
+ `The number of nodes in the list is in the range [1, 100]`
+ `1 <= Node.val <= 100`

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
    ListNode* middleNode(ListNode* head) {
        ListNode* mid = head;
        ListNode* last = head;
        while( last != NULL && last->next != NULL){
            mid = mid -> next ;
            last = last -> next -> next ;
        }
        return mid;
    }
    
};
```
