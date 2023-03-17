---
layout: post
title: Check Completeness of a Binary Tree
summary:
tags:
  - leetcode
  - bfs
  - tree
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/check-completeness-of-a-binary-tree/description/)

Given the root of a binary tree, determine if it is a complete binary tree.

In a complete binary tree, every level, except possibly the last, is completely filled, and all nodes in the last level are as far left as possible. It can have between 1 and 2h nodes inclusive at the last level h.


### Examples

**Example 1:**  

<img src="https://assets.leetcode.com/uploads/2018/12/15/complete-binary-tree-1.png">

```
Input: root = [1,2,3,4,5,6]
Output: true
Explanation: Every level before the last is full (ie. levels with node-values {1} and {2, 3}), and all nodes in the last level ({4, 5, 6}) are as far left as possible.
```

**Example 2:**  

<img src="https://assets.leetcode.com/uploads/2018/12/15/complete-binary-tree-2.png">

```
Input: root = [1,2,3,4,5,null,7]
Output: false
Explanation: The node with value 7 isn't as far left as possible.
```

### Constraints

- The number of nodes in tree is in the range `[1, 100]`.
- `1 <= Node.val <= 1000`

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
    bool isCompleteTree(TreeNode* root) {
        if(!root) {
            return true;
        }
        queue<TreeNode*> q;
        q.push(root);
        while(q.front() != nullptr) {
            auto node = q.front();
            q.pop();
            q.push(node->left);
            q.push(node->right);
        }
        while(!q.empty() && q.front() == nullptr) {
            q.pop();
        }
        return q.empty();
    }
};

```