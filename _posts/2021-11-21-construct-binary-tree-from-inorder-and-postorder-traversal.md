---
layout: post
title: Construct Binary Tree from Inorder and Postorder Traversal
summary:
tags:
    - array
    - binary-tree
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal)  

Given two integer arrays `inorder` and `postorder` where `inorder` is the inorder traversal of a binary tree and `postorder` is the postorder traversal of the same tree, construct and return *the binary tree.*



### Examples

**Example 1:**   
<img src="https://assets.leetcode.com/uploads/2021/02/19/tree.jpg">
```
Input: inorder = [9,3,15,20,7], postorder = [9,15,7,20,3]
Output: [3,9,20,null,null,15,7]
```

**Example 2:**    
```
Input: inorder = [-1], postorder = [-1]
Output: [-1]
```

### Constraints
+ `1 <= inorder.length <= 3000`
+ `postorder.length == inorder.length`
+ `-3000 <= inorder[i], postorder[i] <= 3000`
+ `inorder` and `postorder` consist of unique values.
+ Each value of `postorder` also appears in inorder.
+ `inorder` is guaranteed to be the inorder traversal of the tree.
+ `postorder` is guaranteed to be the postorder traversal of the tree.

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
    int xi;
    vector<int> in, post;
    TreeNode* rc(int l, int r){
      if(l>r) return NULL;
      int i = 0;
      while(in[i]!=post[xi]) i++;
      xi--;
      TreeNode* node = new TreeNode(in[i]);
      node->right = rc(i+1,r);
      node->left = rc(l,i-1);
      return node;
    }
    TreeNode* buildTree(vector<int>& inorder, vector<int>& postorder) {
      in = inorder;
      post = postorder;
      xi = post.size()-1;
      return rc(0, in.size()-1);
    }
};
```

