---
layout: post
title: Symmetric Tree
summary:
tags:
  - leetcode
  - dfs
  - bfs
  - tree
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/symmetric-tree/description/)

Given the root of a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).


### Examples

**Example 1:**  

<img src="https://assets.leetcode.com/uploads/2021/02/19/symtree1.jpg">

```
Input: root = [1,2,2,3,4,4,3]
Output: true
```

**Example 2:**  

<img src="https://assets.leetcode.com/uploads/2021/02/19/symtree2.jpg">

```
Input: root = [1,2,2,null,3,null,3]
Output: false
```

### Constraints

- The number of nodes in head is in the range `[1, 1000]`.
- `-100 <= Node.val <= 100`

## Solutions

```cpp

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
public:
    bool isSymmetric(TreeNode* root) {
        if(root == NULL) return true;
        queue<TreeNode*> q;
        q.push(root->left);
        q.push(root->right);
        while(!q.empty()){
            TreeNode* x = q.front();
            q.pop();
            TreeNode* y = q.front();
            q.pop();

            if(x==NULL && y==NULL) continue;
            if(x==NULL || y==NULL || x->val != y->val) return false;
            q.push(x->left);
            q.push(y->right);
            q.push(x->right);
            q.push(y->left);
        }
        return true;
    }
};
```
