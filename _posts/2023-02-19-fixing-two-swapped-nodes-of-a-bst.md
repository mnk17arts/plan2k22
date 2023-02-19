---
layout: post
title: Fixing Two Swapped nodes of a BST
summary:
tags:
  - tree
  - bst
  - geeksforgeeks
  - cpp
  - hard
minute: 10 min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/fixed-two-nodes-of-a-bst/0/?track=DSASP-BST&batchId=154#)

You are given the root of a binary search tree(BST), where exactly two nodes were swapped by mistake. Fix (or correct) the BST by swapping them back. Do not change the structure of the tree.
Note: It is guaranteed that the given input will form BST, except for 2 nodes that will be wrong.

**Your Task:**
You don't need to take any input. Just complete the function `correctBst()` that takes root node as parameter. The function should return the root of corrected BST. BST will then be checked by driver code and 0 or 1 will be printed.

**Expected Time Complexity:** `O(n)`  
**Expected Auxiliary Space:** `O(logn)`

### Examples

**Example 1:**

```
Input:
       10
     /    \
    5      8
   / \
  2   20
Output: 1
Explanation:
```

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20190528095934/FixNodes.jpg">

**Example 2:**

```
Input:
         11
       /    \
      3      17
       \    /
        4  10
Output: 1
Explanation:
By swapping nodes 11 and 10, the BST
can be fixed.
```

### Constraints

- `1 <= N <= 10^5`

## Solutions

```cpp

/*struct Node
{
    int data;
    struct Node *left, *right;
};*/

class Solution {
    void helper(struct Node *root, struct Node *&pre, struct Node *&n1, struct Node *&n2) {
        if(!root) {
            return;
        }
        helper(root->left, pre, n1, n2);
        if(pre && pre->data > root->data) {
            if(!n1) {
                n1 = pre;
            }
            n2 = root;
        }
        pre = root;
        helper(root->right, pre, n1, n2);
    }
  public:
    struct Node *correctBST(struct Node *root) {
        // code here
        Node *pre = NULL, *n1=NULL, *n2=NULL;
        helper(root, pre, n1, n2);
        if(n1 && n2) {
            swap(n1->data, n2->data);
        }
        return root;
    }
};

```
