---
layout: post
title: Insert a node in a BST           
summary:
tags:
    - tree
    - bst
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/insert-a-node-in-a-bst/0/?track=DSASP-BST&batchId=154#)  

Given a BST and a key K. If K is not present in the BST, Insert a new Node with a value equal to K into the BST. 
Note: If K is already present in the BST, don't modify the BST.


**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `insert()` which takes the root of the BST and Key K as input parameters and returns the root of the modified BST after inserting K. 
Note: The generated output contains the inorder traversal of the modified tree.

**Expected Time Complexity:** `O(h)`      
**Expected Auxiliary Space:** `O(h)`  

### Examples

**Example 1:**   
```
Input:
        2
      /   \
     1     3
             \
              6
K = 4
Output: 1 2 3 4 6
Explanation: After inserting the node 4
Inorder traversal of the above tree
will be 1 2 3 4 6.
```


**Example 2:**   
```
Input:
     2
   /   \
  1     3
K = 4
Output: 1 2 3 4
Explanation: After inserting the node 4
Inorder traversal will be 1 2 3 4.

```


### Constraints

+ `1 <= Number of nodes <= 10^5`
+ `1 <= K <= 10^6`

## Solutions

```cpp
// Function to insert a node in a BST.
Node* insert(Node* root, int Key) {
    // Your code here
    if (root == NULL) {
        root = new Node(Key);
        return root;
    }
    if (Key < root->data)
        root->left = insert(root->left, Key);
    else if (Key > root->data)
        root->right = insert(root->right, Key);
    return root;
}
```

