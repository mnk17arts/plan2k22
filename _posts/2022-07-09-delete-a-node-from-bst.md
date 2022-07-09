---
layout: post
title: Delete a node from BST             
summary:
tags:
    - tree
    - bst
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](hhttps://practice.geeksforgeeks.org/problems/delete-a-node-from-bst/0/?track=DSASP-BST&batchId=154#)  

Given a Binary Search Tree and a node value X. Delete the node with the given value X from the BST. If no node with value x exists, then do not make any change. 


**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `deleteNode()` which takes two arguments. The first being the root of the tree, and an integer '`X`' denoting the node value to be deleted from the BST. Return the root of the BST after deleting the node with value `X`. Do not make any update if there's no node with value `X` present in the BST.

Note: The generated output will be the inorder traversal of the modified tree.


**Expected Time Complexity:** `O(h)`      
**Expected Auxiliary Space:** `O(h)`  

### Examples

**Example 1:**   
```
Input:
            1
             \
              2
                \
                 8 
               /    \
              5      11
            /  \    /  \
           4    7  9   12
X = 9
Output: 1 2 4 5 7 8 11 12
Explanation: In the given input tree after
deleting 9 will be
             1
              \
               2
                 \
                  8
                 /   \
                5     11
               /  \     \
              4    7     12
```


**Example 2:**   
```
Input:
      2
    /   \
   1     3
X = 12
Output: 1 2 3
Explanation: In the given input there
is no node with value 12 , so the tree
will remain same.
```


### Constraints

+ `1 <= Number of nodes <= 10^5`

## Solutions

```cpp
// Function to delete a node from BST.
Node *deleteNode(Node *root, int X) {
    // your code goes here
    if(!root) return NULL;
    if(root->data > X) root->left = deleteNode(root->left,X);
    else if(root->data < X) root->right = deleteNode(root->right,X);
    else{
        if(!root->left&&!root->right) { delete root ; return NULL;}
        if(!root->left) {
            Node* temp = root->right;
            delete root; return temp;
        }
        if(!root->right) {
            Node* temp = root->left;
            delete root; return temp;
        }
        Node* temp = root->right;
        while(temp->left) temp=temp->left;
        root->data = temp->data;
        root->right = deleteNode(root->right, temp->data);

    } 
    return root;
}
```

