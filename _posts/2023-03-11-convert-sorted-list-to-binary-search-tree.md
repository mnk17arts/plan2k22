---
layout: post
title: Convert Sorted List to Binary Search Tree
summary:
tags:
  - leetcode
  - linkedlist
  - divide-conquer
  - bst
  - tree
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/convert-sorted-list-to-binary-search-tree/description/)

Given the head of a singly linked list where elements are sorted in ascending order, convert it to a height-balanced binary search tree.


### Examples

**Example 1:**  

<img src="https://assets.leetcode.com/uploads/2020/08/17/linked.jpg">

```
Input: head = [-10,-3,0,5,9]
Output: [0,-3,9,-10,null,5]
Explanation: One possible answer is [0,-3,9,-10,null,5], which represents the shown height balanced BST.
```

**Example 2:**  

```
Input: head = []
Output: []
```

### Constraints

- The number of nodes in head is in the range `[0, 2 * 10^4]`.
- `-10^5 <= Node.val <= 10^5`

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
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
    TreeNode* BST(ListNode* head, ListNode* tail) {
        if(head == tail) {
            return NULL;
        }
        ListNode *slow = head, *fast = head;
        while(fast != tail && fast->next != tail) {
            slow = slow->next;
            fast = fast->next->next;
        }
        TreeNode* root = new TreeNode(slow->val);
        root->left = BST(head, slow);
        root->right = BST(slow->next, tail);
        return root;
    }
public:
    TreeNode* sortedListToBST(ListNode* head) {
        if(!head) {
            return NULL;
        }
        if(!head->next) {
            return new TreeNode(head->val);
        }
        return BST(head, NULL);
    }
};

```
