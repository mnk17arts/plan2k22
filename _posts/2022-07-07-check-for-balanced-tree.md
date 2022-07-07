---
layout: post
title: Check for Balanced Tree          
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/check-for-balanced-tree/0/)  

Given a binary tree, find if it is height balanced or not. 
A tree is height balanced if difference between heights of left and right subtrees is not more than one for all nodes of tree. 

```
A height balanced tree
        1
     /     \
   10      39
  /
5

An unbalanced tree
        1
     /    
   10   
  /
5    
```


**Your Task:** 
You don't need to take input. Just complete the function `isBalanced()` that takes root node as parameter and returns true, if the tree is balanced else returns false.  

**Expected Time Complexity:** `O(N)`      
**Expected Auxiliary Space:** `O(h)`   where `h` is height of tree 

### Examples

**Example 1:**   
```
Input:
       10
     /   \
    20   30 
  /   \
 40   60
Output: 1
Explanation: The max difference in height
of left subtree and right subtree is 1.
Hence balanced. 
```


**Example 2:**   
```
Input:
      1
    /
   2
    \
     3 
Output: 0
Explanation: The max difference in height
of left subtree and right subtree is 2,
which is greater than 1. Hence unbalanced
```


### Constraints

+ `1 <= Number of nodes <= 10^5`
+ `0 <= Data of a node <= 10^6`

## Solutions

```cpp
class Solution{
    public:
    //Function to check whether a binary tree is balanced or not.
    int height(Node* root){
        if(!root) return 0;
        int lh = height(root->left);
        if(lh==-1) return -1;
        int rh = height(root->right);
        if(rh==-1) return -1;
        if(abs(lh-rh)>1) return -1;
        return max(lh,rh)+1;
    }
    bool isBalanced(Node *root)
    {
        //  Your Code here
        return height(root)!=-1;
    }
};
```

