---
layout: post
title: Linked List Cycle II
summary:
tags:
  - leetcode
  - hash
  - linkedlist
  - 2pointers
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/linked-list-cycle-ii/description/)

Given the head of a linked list, return the node where the cycle begins. If there is no cycle, return null.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally, pos is used to denote the index of the node that tail's next pointer is connected to (0-indexed). It is -1 if there is no cycle. Note that pos is not passed as a parameter.

Do not modify the linked list.


### Examples

**Example 1:**  

<img src="https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png">

```
Input: head = [3,2,0,-4], pos = 1
Output: tail connects to node index 1
Explanation: There is a cycle in the linked list, where tail connects to the second node.
```

**Example 2:**  

<img src="https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test2.png">

```
Input: head = [1,2], pos = 0
Output: tail connects to node index 0
Explanation: There is a cycle in the linked list, where tail connects to the first node.
```

**Example 3:**

<img src="https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test3.png">

```
Input: head = [1], pos = -1
Output: no cycle
Explanation: There is no cycle in the linked list.
```

### Constraints

- The number of the nodes in the list is in the range `[0, 10^4]`.
- `-10^5 <= Node.val <= 10^5`
- `pos` is `-1` or a **valid index** in the linked-list.

## Solutions

```cpp

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode *detectCycle(ListNode *head) {
        if (head == nullptr)return nullptr;
        ListNode* slow1 = head;
        ListNode* slow2 = head;
        ListNode* fast = head;
        
        while (fast -> next != nullptr && fast -> next -> next!=nullptr){
            fast = fast -> next -> next; slow1 = slow1 -> next;
            if (slow1 == fast){//slow and fast meeting point B found.
                while (slow1 != slow2)
                    slow1 = slow1 -> next, slow2 = slow2 -> next;
                return slow1;
            }
        }
        return nullptr;
    }
};

```
