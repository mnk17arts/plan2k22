---
layout: post
title: Find Duplicate Subtrees
summary:
tags:
  - leetcode
  - hash
  - tree
  - dfs
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/find-duplicate-subtrees/description/)

Given the root of a binary tree, return all duplicate subtrees.

For each kind of duplicate subtrees, you only need to return the root node of any one of them.

Two trees are duplicate if they have the same structure with the same node values.


### Examples

**Example 1:**  

<img src="https://assets.leetcode.com/uploads/2020/08/16/e1.jpg">

```
Input: root = [1,2,3,4,null,2,4,null,null,4]
Output: [[2,4],[4]]
```

**Example 2:**  

<img src="https://assets.leetcode.com/uploads/2020/08/16/e2.jpg">

```
Input: root = [2,1,1]
Output: [[1]]
```

**Example 3:**

<img src="https://assets.leetcode.com/uploads/2020/08/16/e33.jpg">

```
Input: root = [2,2,2,3,null,3,null]
Output: [[2,3],[3]]
```

### Constraints

- The number of the nodes in the tree will be in the range `[1, 5000]`
- `-200 <= Node.val <= 200`

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
    string util(unordered_map<string, vector<TreeNode*>> &map, TreeNode* &root) {
        if(!root) {
            return "";
        }
        string str = "{" + util(map, root->left) + to_string(root->val) + util(map, root->right) + "}";
        map[str].push_back(root);
        return str;
    }
public:
    vector<TreeNode*> findDuplicateSubtrees(TreeNode* root) {
        unordered_map<string, vector<TreeNode*>> map;
        vector<TreeNode*> res;
        util(map, root);
        for(const auto &it: map) {
            if(it.second.size() > 1) {
                res.push_back(it.second[0]);
            }
        }
        return res;
    }
};

```
