---
layout: post
title: Postorder Traversal       
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/postorder-traversal/0)  

Given a binary tree, find the Postorder Traversal of it.
For Example, the postorder traversal of the following tree is:
```
5 10 39 1

        1
     /     \
   10     39
  /
5
```


**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `postOrder()` that takes root node as input and returns an array containing the postorder traversal of the given Binary Tree.

**Expected Time Complexity:** `O(N)` 
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input:
        19
     /     \
    10      8
  /    \
 11    13
Output: 11 13 10 8 19
```

**Example 2:**   
```
Input:
          11
         /
       15
      /
     7
Output: 7 15 11
```


### Constraints

+ `1 <= Number of nodes <= 10^5`
+ `0 <= Data of a node <= 10^6`

## Solutions

```cpp

void postOrderT(Node* root, vector<int> &res){
    if(!root) return;
    postOrderT(root->left, res);
    postOrderT(root->right, res);
    res.push_back(root->data);
}
//Function to return a list containing the postorder traversal of the tree.
vector <int> postOrder(Node* root)
{
  // Your code here
  vector<int> res;
  postOrderT(root, res);
  return res;
}
```

