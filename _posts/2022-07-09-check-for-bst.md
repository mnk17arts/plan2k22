---
layout: post
title: Check for BST           
summary:
tags:
    - tree
    - bst
    - geeksforgeeks
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/check-for-bst/0/?track=DSASP-BST&batchId=154#)  

Given the root of a binary tree. Check whether it is a BST or not.
Note: We are considering that BSTs can not contain duplicate Nodes.

A BST is defined as follows:

+ The left subtree of a node contains only nodes with keys less than the node's key.
+ The right subtree of a node contains only nodes with keys greater than the node's key.
+ Both the left and right subtrees must also be binary search trees.


**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `isBST()` which takes the root of the tree as a parameter and returns true if the given binary tree is BST, else returns false. 

**Expected Time Complexity:** `O(N)`      
**Expected Auxiliary Space:** `O(h)`  

### Examples

**Example 1:**   
```
Input:
  2
   \
    7
     \
      6
       \
        5
         \
          9
           \
            2
             \
              6
Output: 0 
Explanation: 
Since the node with value 7 has right subtree 
nodes with keys less than 7, this is not a BST.
```   

**Example 2:**   
```
Input:
   2
 /    \
1      3
Output: 1 
Explanation: 
The left subtree of root node contains node
with key lesser than the root nodes key and 
the right subtree of root node contains node 
with key greater than the root nodes key.
Hence, the tree is a BST.
```


### Constraints

+ `1 <= Number of nodes <= 10^5`
+ `1 <= data <= 10^5`

## Solutions

```cpp
class Solution
{
    public:
    //Function to check whether a Binary Tree is BST or not.
    bool isBST(Node* root, int mn=INT_MIN, int mx=INT_MAX) 
    {
        // Your code here
        return root && root->data < mx && root->data > mn &&
                isBST(root->left,mn,root->data) &&
                isBST(root->right,root->data,mx) || !root;
    }

};
```

