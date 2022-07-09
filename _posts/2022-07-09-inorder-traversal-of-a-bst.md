---
layout: post
title: Inorder traversal of a BST          
summary:
tags:
    - tree
    - bst
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/inorder-traversal-of-a-bst/0/?track=DSASP-BST&batchId=154#)  

Inorder traversal means traversing through the tree in a Left, Node, Right manner. We first traverse left, then print the current node, and then traverse right. This is done recursively for each node.
Given a BST, find its in-order traversal.


**Your Task:** 
You don't need to read input or print anything. Complete the function `inOrder()` that takes the root of the BST as input parameter and returns a list of integers containing the in-order traversal of the BST.

**Expected Time Complexity:** `O(N)`      
**Expected Auxiliary Space:** `O(h)`  

### Examples

**Example 1:**   
```
Input:
     30
     /
   10
     \
     20
Output: 10 20 30
```


**Example 2:**   
```
Input:
       5
    /    \
   2      7
    \       \
    3        8
Output: 2 3 5 7 8

```


### Constraints

+ `1 <= Number of nodes <= 100`
+ `0 <= Data of a node <= 100`

## Solutions

```cpp
// Function to return a list containing the inorder traversal of the BST.
vector<int> inOrder(Node *root) {
    // code here
    vector<int> v;
    if (root == NULL)
        return v;
    vector<int> left = inOrder(root->left);
    v.insert(v.end(), left.begin(), left.end());
    v.push_back(root->data);
    vector<int> right = inOrder(root->right);
    v.insert(v.end(), right.begin(), right.end());
    return v;
}
```

