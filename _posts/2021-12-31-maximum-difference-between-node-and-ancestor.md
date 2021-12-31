---
layout: post
title: Maximum Difference Between Node and Ancestor
summary:
tags:
    - tree
    - dfs
    - leetcode
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/maximum-difference-between-node-and-ancestor)  

Given the root of a binary tree, find the maximum value `v` for which there exist different nodes `a` and `b` where `v = |a.val - b.val|` and `a` is an ancestor of `b`.

A node `a` is an ancestor of `b` if either: any child of `a` is equal to `b` or any child of `a` is an ancestor of `b`.


### Examples

**Example 1:**   
<img src="https://assets.leetcode.com/uploads/2020/11/09/tmp-tree.jpg">
```
Input: root = [8,3,10,1,6,null,14,null,null,4,7,13]
Output: 7
Explanation: We have various ancestor-node differences, some of which are given below :
|8 - 3| = 5
|3 - 7| = 4
|8 - 1| = 7
|10 - 13| = 3
Among all possible differences, the maximum value of 7 is obtained by |8 - 1| = 7.
```

**Example 2:**  
<img src="https://assets.leetcode.com/uploads/2020/11/09/tmp-tree-1.jpg">
```
Input: root = [1,null,2,null,0,3]
Output: 3
```

### Constraints

+ The number of nodes in the tree is in the range `[2, 5000]`.
+ `1 <= Node.val <= 10^5`

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
    int maxAncestorDiff(TreeNode* root) {
      if(!root) return 0;
      return rc(root, root->val, root->val);
    }
    int rc(TreeNode* root, int mn, int mx){
      if(!root) return mx-mn;
      mx = max(mx, root->val);
      mn = min(mn, root->val);
      int l = rc(root->left, mn, mx);
      int r = rc(root->right, mn, mx);
      return max(l, r);
    }
};
```

