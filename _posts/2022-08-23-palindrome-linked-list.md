---
layout: post
title: Palindrome Linked List                       
summary:
tags:
    - leetcode
    - linked-list
    - recursion
    - 2pointers
    - stack
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/palindrome-linked-list/)  

Given the `head` of a singly linked list, return `true` if it is a palindrome.


### Examples

<img src="https://assets.leetcode.com/uploads/2021/03/03/pal1linked-list.jpg">

**Example 1:**   
```
Input: head = [1,2,2,1]
Output: true
```

<img src="https://assets.leetcode.com/uploads/2021/03/03/pal2linked-list.jpg">

**Example 2:**   
```
Input: head = [1,2]
Output: false
```


### Constraints

+ `The number of nodes in the list is in the range [1, 10^5].`
+ `0 <= Node.val <= 9`

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
    ListNode* reverse(ListNode* head) {
        ListNode* prev = nullptr;
        ListNode* curr = head;
        while (curr) {
            ListNode* next = curr->next;
            curr->next = prev;
            prev = curr;
            curr = next;
        }
        return prev;
    }

    bool isPalindrome(ListNode* head) {
        if(!head) return true;
        ListNode* slow = head;
        ListNode* fast = head;
        while(fast && fast->next){
            slow = slow->next;
            fast = fast->next->next;
        }
        if(fast) slow = slow->next;
        slow = reverse(slow);
        while(slow){
            if(head->val != slow->val) return false;
            head = head->next;
            slow = slow->next;
        }
        return true;
    }
};
```

