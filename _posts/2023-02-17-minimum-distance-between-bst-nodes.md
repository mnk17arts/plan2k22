---
layout: post
title: Minimum Distance Between BST Nodes
summary:
tags:
  - leetcode
  - tree
  - dfs
  - bfs
  - bst
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/minimum-distance-between-bst-nodes/)

Given the root of a Binary Search Tree (BST), return the minimum absolute difference between the values of any two different nodes in the tree.

### Examples

**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2021/02/05/bst1.jpg">

```
Input: root = [4,2,6,1,3]
Output: 1
```

**Example 2:**  
<img src="https://assets.leetcode.com/uploads/2021/02/05/bst2.jpg">

```
Input: root = [1,0,48,null,null,12,49]
Output: 1
```

### Constraints

- The number of nodes in the tree is in the range `[2, 100]`
- `0 <= Node.val <= 10^5`

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
    int minDiffInBST(TreeNode* root) {
        int res = INT_MAX;
        stack<TreeNode*> st;
        TreeNode* cur = root, *pre = nullptr;
        while(cur || st.size()) {
            if(cur) {
                st.push(cur);
                cur = cur->left;
            }
            else {
                cur = st.top();
                st.pop();
                if(pre) {
                    res = min(res, cur->val - pre->val);
                }
                pre = cur;
                cur = cur->right;
            }
        }
        return res;
    }
};

```
