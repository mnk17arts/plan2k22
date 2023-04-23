---
layout: post
title: Convert Sorted Array to Binary Search Tree
summary:
tags:
  - leetcode
  - tree
  - bst
  - array
  - cpp
  - easy
minute: 5+ min
---

## Problem Statement - [_link_](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/description/)

Given an integer array nums where the elements are sorted in ascending order, convert it to a height-balanced binary search tree.


### Examples

**Example 1:**  

<img src="https://assets.leetcode.com/uploads/2021/02/18/btree1.jpg">

```
Input: nums = [-10,-3,0,5,9]
Output: [0,-3,9,-10,null,5]
Explanation: [0,-10,5,null,-3,null,9] is also accepted:
```
<img src="https://assets.leetcode.com/uploads/2021/02/18/btree2.jpg">

**Example 2:**  

<img src="https://assets.leetcode.com/uploads/2021/02/18/btree.jpg">

```
Input: nums = [1,3]
Output: [3,1]
Explanation: [1,null,3] and [3,1] are both height-balanced BSTs.
```

### Constraints

- `1 <= nums.length <= 10^4`
- `-10^4 <= nums[i] <= 10^4`
- `nums` is sorted in a **strictly increasing** order.

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
    TreeNode* convertintoBST(vector<int> &nums,int left,int right) {
        if(left > right) return NULL;
        int mid = left+(right-left)/2;
        TreeNode *node = new TreeNode(nums[mid]);
        node->left = convertintoBST(nums,left,mid-1);
        node->right = convertintoBST(nums,mid+1,right);
        return node;
    }
    TreeNode* sortedArrayToBST(vector<int>& nums) {
        if(nums.size() == 0) return NULL;
        return convertintoBST(nums,0,nums.size()-1);
    }
};

```
