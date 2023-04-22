---
layout: post
title: Binary Tree Inorder Traversal
summary:
tags:
  - leetcode
  - tree
  - dfs
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/binary-tree-inorder-traversal/description/)

Given the root of a binary tree, return the inorder traversal of its nodes' values.


### Examples

**Example 1:**  

<img src="https://assets.leetcode.com/uploads/2020/09/15/inorder_1.jpg">

```
Input: root = [1,null,2,3]
Output: [1,3,2]
```

**Example 2:**  

```
Input: root = []
Output: []
```

**Example 3:**  

```
Input: root = [1]
Output: [1]
```

### Constraints

- The number of nodes in the tree is in the range `[0, 100]`.
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
    vector<int> ans;
public:
    void helper(TreeNode* root)
    {
        if(!root) return;
        helper(root->left);
        ans.push_back(root->val);
        helper(root->right);
    }

    vector<int> inorderTraversal(TreeNode* root) {
        helper(root);
        return ans;
    }
};

```
