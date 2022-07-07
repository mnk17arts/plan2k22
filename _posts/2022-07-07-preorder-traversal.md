---
layout: post
title: Preorder Traversal       
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/preorder-traversal/0/?)  

Given a binary tree, find its preorder traversal.


**Your Task:** 
You just have to complete the function `preorder()` which takes the root node of the tree as input and returns an array containing the preorder traversal of the tree.

**Expected Time Complexity:** `O(N)` 
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input:
        1      
      /          
    4    
  /    \   
4       2
Output: 1 4 4 2 
```

**Example 2:**   
```
Input:
       6
     /   \
    3     2
     \   / 
      1 2
Output: 6 3 1 2 2 
```


### Constraints

+ `1 <= Number of nodes <= 10^4`
+ `0 <= Data of a node <= 10^5`

## Solutions

```cpp
void preorderTraversal(Node* root, vector<int> &res){
    if(!root)return;
    res.push_back(root->data);
    preorderTraversal(root->left, res);
    preorderTraversal(root->right, res);
}

vector<int> preorder(Node* root) {
  // Your code here
  vector<int> res;
  preorderTraversal(root, res);
  return res;
}
```

