---
layout: post
title: All Elements in Two Binary Search Trees
summary:
tags:
    - tree
    - dfs
    - binary-tree
    - sorting
    - leetcode
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/all-elements-in-two-binary-search-trees)  

Given two binary search trees `root1` and `root2`, return *a list containing all the integers from both trees sorted in **ascending** order.*


### Examples

**Example 1:**  
<img src="https://assets.leetcode.com/uploads/2019/12/18/q2-e1.png"> 
```
Input: root1 = [2,1,4], root2 = [1,0,3]
Output: [0,1,1,2,3,4]
```

**Example 2:**   
<img src="https://assets.leetcode.com/uploads/2019/12/18/q2-e5-.png">
```
Input: root1 = [1,null,8], root2 = [8,1]
Output: [1,1,8,8]
```

### Constraints

+ The number of nodes in each tree is in the range `[0, 5000]`.
+ `-10^5 <= Node.val <= 10^5`

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
     vector<int> res;
     void dfs(TreeNode *root)
     {
          if (!root)
               return;
          res.push_back(root->val);
          dfs(root->left);
          dfs(root->right);
     }
     vector<int> getAllElements(TreeNode *root1, TreeNode *root2)
     {
          dfs(root1);
          dfs(root2);
          sort(begin(res), end(res));
          return res;
     }
};
```

