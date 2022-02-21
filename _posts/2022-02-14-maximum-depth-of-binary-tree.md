---
layout: post
title: Maximum Depth of Binary Tree
summary:
tags:
    - tree
    - dfs
    - bfs 
    - leetcode
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/maximum-depth-of-binary-tree)  

Given the `root` of a binary tree, return its maximum depth.

A binary tree's **maximum depth** is the number of nodes along the longest path from the root node down to the farthest leaf node.

### Examples

**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2020/11/26/tmp-tree.jpg">
```
Input: root = [3,9,20,null,null,15,7]
Output: 3
```

**Example 2:**  
```
Input: root = [1,null,2]
Output: 2
```

### Constraints

+ The number of nodes in the tree is in the range `[0, 10^4]`.
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
    int maxDepth(TreeNode* root) {
      if(!root) return 0;
      return 1 + max(maxDepth(root->left),maxDepth(root->right));
    }
};
```