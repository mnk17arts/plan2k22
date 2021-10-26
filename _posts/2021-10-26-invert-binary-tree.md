---
layout: post
title:  Invert Binary Tree
description: 
summary: 
tags:
    - tree
    - dfs
    - bfs
    - binary-tree
    - leetcode
    - cpp
    - easy
minute: 2 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/invert-binary-tree/)
Given the `root` of a binary tree, invert the tree, and return *its `root`*.
 
### Examples   
**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2021/03/14/invert1-tree.jpg">
```
Input: root = [4,2,7,1,3,6,9]
Output: [4,7,2,9,6,3,1]
```

**Example 2:**  
<img src="https://assets.leetcode.com/uploads/2021/03/14/invert2-tree.jpg">
```
Input: root = [2,1,3]
Output: [2,3,1]
```

**Example 3:**  
```
Input: root = []
Output: []
```

### Constraints
+ The number of nodes in the tree is in the range `[0, 100]`.
+ `-100 <= Node.val <= 100`


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
    void rc(TreeNode* root){
        if(root==NULL or (!root->left and !root->right)) return;
        TreeNode *post, *pre;
        pre = root->left;
        post = root->right;
        root->left = post;
        root->right = pre;   
        rc(root->left);
        rc(root->right);
    }
    TreeNode* invertTree(TreeNode* root) {
        if(!root) return root;
        rc(root);
        return root;
    }
};
```

