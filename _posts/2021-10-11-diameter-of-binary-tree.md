---
layout: post
title: Diameter of Binary Tree
description: 
summary: 
tags:
    - dfs
    - tree
    - binary-tree
    - leetcode
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/diameter-of-binary-tree/)
Given the `root` of a binary tree, return *the length of the **diameter** of the tree*.

The diameter of a binary tree is the **length** of the longest path between any two nodes in a tree. This path may or may not pass through the `root`.

The **length** of a path between two nodes is represented by the number of edges between them.

### Examples
**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2021/03/06/diamtree.jpg" height="300" >
```
Input: root = [1,2,3,4,5]
Output: 3
Explanation: 3 is the length of the path [4,2,1,3] or [5,2,1,3].
```

**Example 2:**  
```
Input: root = [1,2]
Output: 1
```

### Constraints
+ The number of nodes in the tree is in the range `[1, 10^4]`.
+  `-100 <= Node.val <= 100`

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
    int d;
    
    int findHeight(TreeNode* node){
        if(!node) return 0;
        
        int left = findHeight(node->left);
        int right = findHeight(node->right);
        
        d = max(d,left+right);
        
        return max(left, right)+1;
    }
    
    int diameterOfBinaryTree(TreeNode* root) {
        d = 0;
        findHeight(root);
        return d;
    }
};
```
