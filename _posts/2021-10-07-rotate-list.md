---
layout: post
title: Rotate List
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

## Problem Statement - [*link*](https://leetcode.com/problems/rotate-list/)
Given the `head` of a linked list, rotate the list to the right by `k` places.

 

### Examples
**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2020/11/13/rotate1.jpg" height="250">  
```
Input: head = [1,2,3,4,5], k = 2
Output: [4,5,1,2,3]
```

**Example 2:**  
<img src="https://assets.leetcode.com/uploads/2020/11/13/roate2.jpg" height="250">  
```
Input: head = [0,1,2], k = 4
Output: [2,0,1]
```

### Constraints
+ The number of nodes in the list is in the range `[0, 500]`
+ `-100 <= Node.val <= 100`
+ `0 <= k <= 2 * 109`

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
    ListNode* rotateRight(ListNode* head, int k) {
        
        int i = 1,j;
        
        if(head == NULL) return head;
        
        ListNode* right = head;
        
        ListNode* left;
        
        while( right->next != NULL){
            right = right->next;
            i++;
        }
        
        k = k % i;
        
        if(k == 0) return head;
        
        ListNode* temp = head;
        
        j = i-k-1;
        
        while(j--)temp = temp->next;
        
        left = temp->next;
        
        temp->next = NULL;
        
        right->next = head;
        
        return left;  
    }
};
```
