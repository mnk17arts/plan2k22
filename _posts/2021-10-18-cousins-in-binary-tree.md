---
layout: post
title:  Cousins in Binary Tree
description: 
summary: 
tags:
    - tree
    - bfs
    - dfs
    - leetcode
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/cousins-in-binary-tree/)
Given the `root` of a binary tree with unique values and the values of two different nodes of the tree `x` and `y`, return `true` if the nodes corresponding to the values `x` and `y` in the tree are cousins, or `false` otherwise.

Two nodes of a binary tree are cousins if they have the same depth with different parents.

Note that in a binary tree, the root node is at the depth `0`, and children of each depth `k` node are at the depth `k + 1`.

### Examples   

**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2019/02/12/q1248-01.png">
```
Input: root = [1,2,3,4], x = 4, y = 3
Output: false
```

**Example 2:**  
<img src="https://assets.leetcode.com/uploads/2019/02/12/q1248-02.png" >
```
Input: root = [1,2,3,null,4,null,5], x = 5, y = 4
Output: true
```

**Example 3:**  
<img src="https://assets.leetcode.com/uploads/2019/02/13/q1248-03.png" >
```
Input: root = [1,2,3,null,4], x = 2, y = 3
Output: false
```

### Constraints
+ The number of nodes in the tree is in the range `[2, 100]`.
+ `1 <= Node.val <= 100`
+ Each node has a unique value.
+ `x != y`
+ `x` and `y` are exist in the tree.

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
    
    int xd,yd ;
    TreeNode *xp,*yp;
    
    void rc(TreeNode* root, TreeNode* p, int x, int y, int d){
        
        if(!root) return;
        
        if(x == root->val){
            xd = d;
            xp = p;
        }
        else if(y == root->val){
            yd = d;
            yp = p;
        }
        
        rc(root->left, root, x, y, d+1);
        rc(root->right, root, x, y, d+1);
        
    }
    
    bool isCousins(TreeNode* root, int x, int y) {
        
        rc(root, NULL, x, y,0);
        
        return xd==yd and xp!=yp;
    }
    
};
```

