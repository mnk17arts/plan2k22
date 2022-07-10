---
layout: post
title:  Fixing Two nodes of a BST             
summary:
tags:
    - tree
    - bst
    - geeksforgeeks
    - cpp
    - hard
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/fixed-two-nodes-of-a-bst/0/?track=DSASP-BST&batchId=154#)  

You are given the root of a binary search tree(BST), where exactly two nodes were swapped by mistake. Fix (or correct) the BST by swapping them back. Do not change the structure of the tree.
Note: It is guaranteed that the given input will form BST, except for 2 nodes that will be wrong. All changes must be reflected in the original linked list.


**Your Task:** 
You don't need to take any input. Just complete the function `correctBst()` that takes root node as parameter. The function should not return anything, all the changes must be done in the existing tree only. BST will then be checked by driver code and 0 or 1 will be printed.



**Expected Time Complexity:** `O(n)`           
**Expected Auxiliary Space:** `O(1)`


### Examples

**Example 1:**   
```
Input:
       10
     /    \
    5      8
   / \
  2   20
Output: 1
Explanation:
``` 
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20190528095934/FixNodes.jpg">


**Example 2:**   
```
Input:
         11
       /    \
      3      17
       \    /
        4  10
Output: 1 
Explanation: 
By swapping nodes 11 and 10, the BST 
can be fixed.
```


### Constraints

+ `1 <= N <= 10^3`

## Solutions

```cpp
class Solution
{
    public:
    void helper(Node* root, Node* &pre, Node* &one, Node* &two){
        if(!root) return;
        helper(root->left,pre,one,two);
        if(pre && pre->data > root->data){
            if(!one) one = pre;
            two = root;
        }pre = root;
        helper(root->right,pre,one,two);
    }
    void correctBST( struct Node* root )
    {
        // add code here.
        Node* pre = NULL, *one = NULL, *two = NULL;
        helper(root,pre,one,two);
        if(one&&two) swap(one->data,two->data);
    }
};
```

