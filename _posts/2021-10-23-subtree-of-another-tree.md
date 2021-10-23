---
layout: post
title:  Subarray of another tree
description: 
summary: 
tags:
    - tree
    - leetcode
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/subtree-of-another-tree/)
Given the roots of two binary trees `root` and `subRoot`, return `true` if there is a subtree of `root` with the same structure and node values of `subRoot` and `false` otherwise.

A subtree of a binary tree `tree` is a tree that consists of a node in `tree` and all of this node's descendants. The tree `tree` could also be considered as a subtree of itself.
 
### Examples   
**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2021/04/28/subtree1-tree.jpg">
```
Input: root = [3,4,5,1,2], subRoot = [4,1,2]
Output: true
```

**Example 2:**   
<img src="https://assets.leetcode.com/uploads/2021/04/28/subtree2-tree.jpg">  
``` 
Input: root = [3,4,5,1,2,null,null,null,null,0], subRoot = [4,1,2]
Output: false
```

### Constraints
+ The number of nodes in the `root` tree is in the range `[1, 2000]`.
+ The number of nodes in the `subRoot` tree is in the range `[1, 1000]`.
+ `-10^4 <= root.val <= 10^4`
+ `-10^4 <= subRoot.val <= 10^4`


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
    
    bool check(TreeNode* root, TreeNode* subRoot){
        
        if(!root and !subRoot) return true;
        if(!root or !subRoot or root->val != subRoot->val) return false;
        return check(root->left,subRoot->left) and check(root->right,subRoot->right);
        
    }
    
    bool isSubtree(TreeNode* root, TreeNode* subRoot) {
        
        if(!root) return false;
        if(root->val == subRoot->val and check(root,subRoot)) return true;
        return isSubtree(root->left, subRoot) or isSubtree(root->right, subRoot);
        
    }
    
};
```

