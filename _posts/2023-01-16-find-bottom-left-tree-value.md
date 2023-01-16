---
layout: post
title: Find Bottom Left Tree Value                       
summary:
tags:
    - leetcode
    - tree
    - bfs
    - dfs
    - binary-tree
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/find-bottom-left-tree-value/description/)  

Given the root of a binary tree, return the leftmost value in the last row of the tree.


### Examples


**Example 1:**   

![img](https://assets.leetcode.com/uploads/2020/12/14/tree1.jpg)

```
Input: root = [2,1,3]
Output: 1
```


**Example 2:**   

![img](https://assets.leetcode.com/uploads/2020/12/14/tree2.jpg)

```
Input: root = [1,2,3,4,null,5,6,null,null,7]
Output: 7
```

### Constraints

+ The number of nodes in the tree is in the range `[1, 10^5]`
+ `-2^31 <= Node.val <= 2^31 - 1`

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
    int deepR,deepC,res;
    void helper(TreeNode* root, int r, int c){
        if(root==NULL) return;
        if(r>deepR) { deepR=r; deepC=c; res = root->val;}
        else if (r==deepR && c < deepC) {deepC=c; res = root->val;}
        helper(root->left,r+1,c-1);
        helper(root->right,r+1,c+1);
    }
    int findBottomLeftValue(TreeNode* root) {
        deepR=deepC=0;
        res = root->val;
        helper(root,deepR,deepC);
        return res;
    }
};
```

