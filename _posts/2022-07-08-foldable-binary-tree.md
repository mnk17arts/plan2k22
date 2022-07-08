---
layout: post
title: Foldable Binary Tree           
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/foldable-binary-tree/0/?)  

Given a binary tree, check if the tree can be folded or not. A tree can be folded if left and right subtrees of the tree are structure wise same. An empty tree is considered as foldable.
Consider the below trees:
(a) and (b) can be folded.
(c) and (d) cannot be folded.

```
(a)
       10
     /    \
    7      15
     \    /
      9  11
(b)
        10
       /  \
      7    15
     /      \
    9       11
(c)
        10
       /  \
      7   15
     /    /
    5   11
(d)
         10
       /   \
      7     15
    /  \    /
   9   10  12
```

**Your Task:** 
The task is to complete the function `isFoldable()` that takes root of the tree as input and returns true or false depending upon whether the tree is foldable or not.

**Expected Time Complexity:** `O(N)`      
**Expected Auxiliary Space:** `O(h)`  

### Examples

**Example 1:**   
```
Input:
      10
    /    \
   7     15
 /  \   /  \
5   N  11   N
Output: No 
```


**Example 2:**   
```
Input:
     10
    /    \
   7     15
 /  \   /  \
N   9  11   N
Output:Yes
```


### Constraints

+ `0 <= Number of nodes <= 10^3`
+ `1 <= data <= 10^4`

## Solutions

```cpp
bool isSym(Node* l, Node* r){
    if(!l || !r) return l==r;
    return isSym(l->left,r->right)&&isSym(l->right,r->left);
}
//Function to check whether a binary tree is foldable or not.
bool IsFoldable(Node* root)
{
    // Your code goes here
    if(!root) return true;
    return isSym(root->left, root->right);
}
```

