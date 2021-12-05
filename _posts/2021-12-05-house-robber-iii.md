---
layout: post
title: House Robber III
summary:
tags:
    - tree
    - dynamic-programming
    - dfs
    - leetcode
    - cpp
    - medium
minute: 6 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/house-robber-iii)  

The thief has found himself a new place for his thievery again. There is only one entrance to this area, called `root`.

Besides the `root`, each house has one and only one parent house. After a tour, the smart thief realized that all houses in this place form a binary tree. It will automatically contact the police if **two directly-linked houses were broken into on the same night.**

Given the `root` of the binary tree, return *the maximum amount of money the thief can rob **without alerting the police.***

### Examples

**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2021/03/10/rob1-tree.jpg"> 
```
Input: root = [3,2,3,null,3,null,1]
Output: 7
Explanation: Maximum amount of money the thief can rob = 3 + 3 + 1 = 7.
```

**Example 2:**  
<img src="https://assets.leetcode.com/uploads/2021/03/10/rob2-tree.jpg"> 
```
Input: root = [3,4,5,1,3,null,1]
Output: 9
Explanation: Maximum amount of money the thief can rob = 4 + 5 = 9.
```

### Constraints
+ The number of nodes in the tree is in the range `[1, 10^4]`.
+ `0 <= Node.val <= 10^4`


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
  unordered_map<TreeNode*, int> mp;
    int rob(TreeNode* root) {
      if(!root) return 0;
      if(mp[root]) return mp[root];
      int i=root->val;
      if(root->left) i += (rob(root->left->left) + rob(root->left->right));
      if(root->right) i += (rob(root->right->left) + rob(root->right->right));
      int o = rob(root->left) + rob(root->right);
      return mp[root] = max(i,o);
    }
};
```

