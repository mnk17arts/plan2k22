---
layout: post
title: Delete Node in a BST
summary:
tags:
    - binary-tree
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/delete-node-in-a-bst)  

Given a `root` node reference of a BST and a `key`, delete the node with the given key in the BST. Return the root node reference (possibly updated) of the BST.

Basically, the deletion can be divided into two stages:

+ Search for a node to remove.
+ If the node is found, delete the node.

### Examples

**Example 1:**   
<img src="https://assets.leetcode.com/uploads/2020/09/04/del_node_1.jpg">
```
Input: root = [5,3,6,2,4,null,7], key = 3
Output: [5,4,6,2,null,null,7]
Explanation: Given key to delete is 3. So we find the node with value 3 and delete it.
One valid answer is [5,4,6,2,null,null,7], shown in the above BST.
Please notice that another valid answer is [5,2,6,null,4,null,7] and it's also accepted.
```
<img src="https://assets.leetcode.com/uploads/2020/09/04/del_node_supp.jpg">


**Example 2:**    
```
Input: root = [5,3,6,2,4,null,7], key = 0
Output: [5,3,6,2,4,null,7]
Explanation: The tree does not contain a node with value = 0.
```

**Example 3:**    
```
Input: root = [], key = 0
Output: []
```

### Constraints
+ The number of nodes in the tree is in the range `[0, 104]`.
+ `-10^5 <= Node.val <= 10^5`
+ Each node has a unique value.
+ root is a valid binary search tree.
+ `-10^5 <= key <= 10^5`

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
    TreeNode* deleteNode(TreeNode* root, int key) {
      if(root){
        if(root->val > key) root->left = deleteNode(root->left, key);
        else if(root->val < key) root->right = deleteNode(root->right, key);
        else{
          if(!root->left and !root->right) return NULL;
          else if(!root->left or !root->right) 
            return root->left ? root->left : root->right;
          TreeNode* t = root->left;
          while(t->right != NULL) t=t->right;
          root->val = t->val;
          root->left = deleteNode(root->left, t->val);          
        }
      }
      return root;
    }
};
```

