---
layout: post
title: Lowest Common Ancestor in a BST             
summary:
tags:
    - tree
    - bst
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/lowest-common-ancestor-in-a-bst/0/?t)  

Given a Binary Search Tree and a node value X. Delete the node with the given value X from the BST. If no node with value x exists, then do not make any change. 


**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `LCA()` which takes the root Node of the BST and two integer values `n1` and `n2` as inputs and returns the Lowest Common Ancestor of the Nodes with values `n1` and `n2` in the given BST. 


**Expected Time Complexity:** `O(h)`      
**Expected Auxiliary Space:** `O(h)`  

### Examples

**Example 1:**   
```
Input:
     2
   /   \
  1     3
n1 = 1, n2 = 3
Output: 2
```


**Example 2:**   
```
Input:
              5
           /    \
         4       6
        /         \
       3           7
                    \
                     8
n1 = 7, n2 = 8
Output: 7
```


### Constraints

+ `1 <= Number of nodes <= 10^4`

## Solutions

```cpp
//Function to find the lowest common ancestor in a BST. 
Node* LCA(Node *root, int n1, int n2)
{
   //Your code here
   if(!root) return NULL;
   if(root->data > n1 && root->data > n2) return LCA(root->left,n1,n2);
   else if(root->data < n1 && root->data < n2) return LCA(root->right,n1,n2);
   else return root;
}
```

