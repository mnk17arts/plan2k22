---
layout: post
title: Sum of Root To Leaf Binary Numbers
summary:
tags:
    - tree
    - binary-tree
    - leetcode
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/sum-of-root-to-leaf-binary-numbers)  

You are given the `root` of a binary tree where each node has a value `0` or `1`. Each root-to-leaf path represents a binary number starting with the most significant bit.

+ For example, if the path is `0 -> 1 -> 1 -> 0 -> 1`, then this could represent `01101` in binary, which is `13`.

For all leaves in the tree, consider the numbers represented by the path from the root to that leaf. Return *the sum of these numbers*.

The test cases are generated so that the answer fits in a **32-bits** integer.


### Examples

**Example 1:**   
<img src="https://assets.leetcode.com/uploads/2019/04/04/sum-of-root-to-leaf-binary-numbers.png">
```
Input: root = [1,0,1,0,1,0,1]
Output: 22
Explanation: (100) + (101) + (110) + (111) = 4 + 5 + 6 + 7 = 22
```

**Example 2:**   
```
Input: root = [0]
Output: 0
```

### Constraints

+ The number of nodes in the tree is in the range `[1, 1000]`
+ `Node.val` is `0` or `1`

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
    int rootToLeaf = 0;
    void preorder(TreeNode *r, int currNumber) {
        if (r != NULL) {
            currNumber = (currNumber << 1) | r->val;
            if (r->left == NULL && r->right == NULL) {
            rootToLeaf += currNumber;
            }
            preorder(r->left, currNumber);
            preorder(r->right, currNumber);
        }
    }

    int sumRootToLeaf(TreeNode* root) {
        preorder(root, 0);
        return rootToLeaf;
    }
};
```

