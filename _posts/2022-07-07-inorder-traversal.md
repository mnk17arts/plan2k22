---
layout: post
title: Inorder Traversal       
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/inorder-traversal/0/)  

Given a Binary Tree, find the In-Order Traversal of it.


**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `inOrder()` that takes root node of the tree as input and returns a list containing the In-Order Traversal of the given Binary Tree.

**Expected Time Complexity:** `O(N)` 
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input:
       1
     /  \
    3    2
Output: 3 1 2
```

**Example 2:**   
```
Input:
        10
     /      \ 
    20       30 
  /    \    /
 40    60  50
Output: 40 20 60 10 50 30
```


### Constraints

+ `1 <= Number of nodes <= 10^4`
+ `0 <= Data of a node <= 10^5`

## Solutions

```cpp
class Solution {
  public:
    void inOrderT(Node* root, vector<int> &res){
        if(!root) return ;
        inOrderT(root->left, res);
        res.push_back(root->data);
        inOrderT(root->right, res);
    }
    // Function to return a list containing the inorder traversal of the tree.
    vector<int> inOrder(Node* root) {
        // Your code here
        vector<int> res;
        inOrderT(root, res);
        return res;
    }
};
```

