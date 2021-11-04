---
layout: post
title: Sum of Left Leaves
description: 
summary:
tags:
    - tree
    - binary-tree
    - dfs
    - bfs
    - leetcode
    - cpp
    - easy
minute: 2 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/sum-of-left-leaves/)
Given the `root` of a binary tree, return *the sum of all left leaves.*

### Examples

**Example 1:**    
<img src="https://assets.leetcode.com/uploads/2021/04/08/leftsum-tree.jpg"> 
```
Input: root = [3,9,20,null,null,15,7]
Output: 24
Explanation: There are two left leaves in the binary tree, with values 9 and 15 respectively.
```

**Example 2:**  
```
Input: root = [1]
Output: 0
```

### Constraints
+ The number of nodes in the tree is in the range `[1, 1000]`.
+ `-1000 <= Node.val <= 1000`

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
  int res = 0;
  void rc(TreeNode* root){
    if(!root or (!root->left and !root->right)) return;
    if(root->left and !root->left->left and !root->left->right) res+= root->left->val;
    rc(root->left);
    rc(root->right);
  }
  int sumOfLeftLeaves(TreeNode* root) {
    rc(root);
    return res;
  }
};
```

