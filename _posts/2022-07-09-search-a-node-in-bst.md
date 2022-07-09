---
layout: post
title: Search a node in a BST           
summary:
tags:
    - tree
    - bst
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/search-a-node-in-bst/0/?)  

Given a Binary Search Tree and a node value X, find if the node with value X is present in the BST or not.


**Your Task:** 
You don't need to read input or print anything. Complete the function `search()` which returns `true` if the node with value `x` is present in the BST else returns `false`.

**Expected Time Complexity:** `O(h)`      
**Expected Auxiliary Space:** `O(1)`  

### Examples

**Example 1:**   
```
Input:      6
             \ 
              8 
             / \ 
            7   9
X = 11
Output: 0
Explanation: As 11 is not present in 
the given nodes , so the output will
be 0.
```


**Example 2:**   
```
Input:         2
                \
                 81 
               /    \ 
             42      87 
              \       \ 
               66      90 
              / 
            45
X = 87
Output: 1
Explanation: As 87 is present in the
given nodes , so the output will be
1.
```


### Constraints

+ `1 <= Number of nodes <= 10^5`

## Solutions

```cpp
// Function to search a node in BST.
bool search(Node* root, int x) {
    // Your code here
    if (root == NULL)
        return false;
    if (root->data == x)
        return true;
    if (x < root->data)
        return search(root->left, x);
    else
        return search(root->right, x);

}
```

