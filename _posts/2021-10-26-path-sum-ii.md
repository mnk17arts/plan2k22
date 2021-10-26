---
layout: post
title:  Path Sum II
description: 
summary: 
tags:
    - tree
    - dfs
    - backtracking
    - binary-tree
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/path-sum-ii/)
Given the `root` of a binary tree and an integer `targetSum`, return *all **root-to-leaf** paths where the sum of the node values in the path equals `targetSum`*. Each path should be returned as a list of the node **values**, not node references.

A **root-to-leaf** path is a path starting from the root and ending at any leaf node. A **leaf** is a node with no children.
 
### Examples   
**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2021/01/18/pathsumii1.jpg">
```
Input: root = [5,4,8,11,null,13,4,7,2,null,null,5,1], targetSum = 22
Output: [[5,4,11,2],[5,8,4,5]]
Explanation: There are two paths whose sum equals targetSum:
5 + 4 + 11 + 2 = 22
5 + 8 + 4 + 5 = 22
```

**Example 2:**  
<img src="https://assets.leetcode.com/uploads/2021/01/18/pathsum2.jpg">
```
Input: root = [1,2,3], targetSum = 5
Output: []
```

**Example 3:**  
```
Input: root = [1,2], targetSum = 0
Output: []
```

### Constraints
+ The number of nodes in the tree is in the range `[0, 5000]`.
+ `-1000 <= Node.val <= 1000`
+ `-1000 <= targetSum <= 1000`


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
    vector<vector<int>> res;
    vector<int> sub;
    void rc(TreeNode* root, int target, int sum){
        if(!root->left and !root->right){
            sub.push_back(root->val);
            sum += root->val;
            if(sum == target) res.push_back(sub);
            sum -= root->val;
            sub.pop_back();
            return;
        }
        if(root->left){
            sub.push_back(root->val);
            rc(root->left, target, sum+root->val);
            sub.pop_back();
        }         
        if(root->right){
            sub.push_back(root->val);
            rc(root->right, target, sum+root->val);
            sub.pop_back();
        } 
    }
    vector<vector<int>> pathSum(TreeNode* root, int targetSum) {
        if(!root) return res;
        rc(root, targetSum, 0);
        return res;
    }
};
```

