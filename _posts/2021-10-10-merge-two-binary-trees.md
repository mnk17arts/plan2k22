---
layout: post
title: Merge Two Binary Trees
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
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/merge-two-binary-trees/)
You are given two binary trees `root1` and `root2`.

Imagine that when you put one of them to cover the other, some nodes of the two trees are overlapped while the others are not. You need to merge the two trees into a new binary tree. The merge rule is that if two nodes overlap, then sum node values up as the new value of the merged node. Otherwise, the NOT null node will be used as the node of the new tree.

Return *the merged tree.*

**Note:** The merging process must start from the root nodes of both trees.


### Examples  

**Example 1:**   
<img src="https://assets.leetcode.com/uploads/2021/02/05/merge.jpg" height="300">  
```
Input: root1 = [1,3,2,5], root2 = [2,1,3,null,4,null,7]
Output: [3,4,5,5,4,null,7]
```

**Example 2:**  
```
Input: root1 = [1], root2 = [1,2]
Output: [2,2]
```

### Constraints
+ The number of nodes in both trees is in the range `[0, 2000]`
+ `-10^4 <= Node.val <= 10^4`

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
    TreeNode* mergeTrees(TreeNode* root1, TreeNode* root2) {
        
        if(root1 == root2 && root2 == NULL) return NULL;
        
        TreeNode* temp = new TreeNode();
        
        if(root1) temp->val += root1->val;
        if(root2) temp->val += root2->val;
        
        temp->left = mergeTrees(root1?root1->left:NULL,root2?root2->left:NULL);
        temp->right = mergeTrees(root1?root1->right:NULL,root2?root2->right:NULL);
        
        return temp;
        
    }
};
```
