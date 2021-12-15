---
layout: post
title: Insertion Sort List
summary:
tags:
    - linkedlist
    - sorting
    - leetcode
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/insertion-sort-list)  

Given the `head` of a singly linked list, sort the list using **insertion sort**, and return *the sorted list's head.*

The steps of the **insertion sort** algorithm:

1. Insertion sort iterates, consuming one input element each repetition and growing a sorted output list.
1. At each iteration, insertion sort removes one element from the input data, finds the location it belongs within the sorted list and inserts it there.
1. It repeats until no input elements remain. 

The following is a graphical example of the insertion sort algorithm. The partially sorted list (black) initially contains only the first element in the list. One element (red) is removed from the input data and inserted in-place into the sorted list with each iteration.

<img src="https://upload.wikimedia.org/wikipedia/commons/0/0f/Insertion-sort-example-300px.gif">

### Examples

**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2021/03/04/sort1linked-list.jpg">
```
Input: head = [4,2,1,3]
Output: [1,2,3,4]
```

**Example 2:**  
<img src="https://assets.leetcode.com/uploads/2021/03/04/sort2linked-list.jpg">
```
Input: head = [-1,5,3,4,0]
Output: [-1,0,3,4,5]
```

### Constraints
+ The number of nodes in the list is in the range `[1, 5000]`.
+ `-5000 <= Node.val <= 5000`

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
    ListNode* insertionSortList(ListNode* head) {
      ListNode* res = NULL;
      while(head){
        ListNode* t = head;
        head = head->next;
        t->next = NULL;
        
        if(!res) res = t;
        else if(res->val >= t->val) t->next = res, res = t;
        else{
          ListNode* f = res;
          while(f->next){
            if(t->val > f->val and t->val <= f->next->val){
              t->next = f->next;
              f->next = t;
              break;
            }
            f = f->next;
          }
          if(f->next==NULL) f->next = t;
        }
      }
      return res;
    }
};
```

