---
layout: post
title:  Path Sum III
description: 
summary: 
tags:
    - tree
    - dfs
    - leetcode
    - cpp
    - medium
minute: 4 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/path-sum-iii/)
Given the `root` of a binary tree and an integer `targetSum`, return *the number of paths where the sum of the values along the path equals `targetSum`.*

The path does not need to start or end at the root or a leaf, but it must go downwards (i.e., traveling only from parent nodes to child nodes).
 
 
### Examples   
**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2021/04/09/pathsum3-1-tree.jpg"> 
```
Input: root = [10,5,-3,3,2,null,11,3,-2,null,1], targetSum = 8
Output: 3
Explanation: The paths that sum to 8 are shown.
```

**Example 2:**  
```
Input: root = [5,4,8,11,null,13,4,7,2,null,null,5,1], targetSum = 22
Output: 3
```

### Constraints
+ The number of nodes in the tree is in the range `[0, 1000]`.
+ `-10^9 <= Node.val <= 10^9`
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
    int rc(TreeNode* root,int sum,int target){
      if(!root) return 0;
      sum += root->val;
      return (sum==target) + rc(root->left,sum,target) + rc(root->right,sum,target);
    }
    int pathSum(TreeNode* root, int targetSum) {
      if(!root) return 0;
      return rc(root,0,targetSum) + pathSum(root->left,targetSum) + pathSum(root->right,targetSum);
    }
};

```

