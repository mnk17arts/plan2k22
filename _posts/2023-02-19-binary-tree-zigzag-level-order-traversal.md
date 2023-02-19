---
layout: post
title: Binary Tree Zigzag Level Order Traversal
summary:
tags:
  - leetcode
  - tree
  - bfs
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal)

Given the root of a binary tree, return the zigzag level order traversal of its nodes' values. (i.e., from left to right, then right to left for the next level and alternate between).

### Examples

**Example 1:**

<img src="https://assets.leetcode.com/uploads/2021/02/19/tree1.jpg">

```
Input: root = [3,9,20,null,null,15,7]
Output: [[3],[20,9],[15,7]]
```

**Example 2:**
```
Input: root = [1]
Output: [[1]]
```

**Example 3:**
```
Input: root = []
Output: []
```

### Constraints

- `-100 <= Node.val <= 100`
- The number of nodes in the tree is in the range `[0, 2000]`.

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
    vector<vector<int>> zigzagLevelOrder(TreeNode* root) {
        vector<vector<int>> res;
        if(!root) {
            return res;
        }
        queue<TreeNode*> q;
        bool even = true;
        q.push(root);
        while(q.size()) {
            int n = q.size();
            vector<int> temp;
            while(n--) {
                TreeNode* cur = q.front(); q.pop();
                temp.push_back(cur->val);
                if(cur->left) {
                    q.push(cur->left);
                }
                if(cur->right) {
                    q.push(cur->right);
                }
            }
            if(!even) {
                reverse(temp.begin(), temp.end());
            }
            res.push_back(temp);
            even = !even;
        }
        return res;

    }
};

```
