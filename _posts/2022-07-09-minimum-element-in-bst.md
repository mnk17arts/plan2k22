---
layout: post
title: Minimum element in BST            
summary:
tags:
    - tree
    - bst
    - geeksforgeeks
    - cpp
    - easy
minute: 3 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/minimum-element-in-bst/0/?track=DSASP-BST&batchId=154)  

Given a Binary Search Tree. The task is to find the minimum element in this given BST.


**Your Task:** 
The task is to complete the function `minValue()` which takes root as the argument and returns the minimum element of BST. If the tree is empty, there is no minimum elemnt, so retutn `-1` in that case.

**Expected Time Complexity:** `O(h)`      
**Expected Auxiliary Space:** `O(h)`  

### Examples

**Example 1:**   
```
Input:
             9
              \
               10
                \
                 11
Output: 9
```


**Example 2:**   
```
Input:
           5
         /    \
        4      6
       /        \
      3          7
     /
    1
Output: 1
```


### Constraints

+ `0 <= Number of nodes <= 10^4`

## Solutions

```cpp
// Function to find the minimum element in the given BST.
int minValue(Node* root) {
    // Code here
    if(!root) return -1;
    while(root->left) root = root->left;
    return root->data;
}
```

