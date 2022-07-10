---
layout: post
title:  LCA of 3 nodes             
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - easy
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/contest/challenge-6-tree-bst/problems/)  

Given a Binary Search Tree and three nodes, find the least common ancestor(LCA) of all the three nodes.


**Your Task:** 
You don't need to take any input. Just complete the function `lca3Nodes()` that takes root, p, q, r as parameters and returns the LCA of the three nodes.


### Examples

**Example 1:**   
```
Input:
           50
         /    \
        40     70
       / \      
      31  45   
p = 40, q = 70, r = 50
Output: 50
Explanation: 50 is LCA of all 3 nodes.
``` 


**Example 2:**   
```
Input:
           50
         /    \
        40     70
       / \    
      31 45   
p = 31, q = 45, r = 70
Output: 50
Explanation: 50 is LCA of all 3 nodes.
```


### Constraints

+ `1 <= N <= 10^5`

## Solutions

```cpp
class Solution {
  public:
    int lca3Nodes(Node* root, int p, int q, int r) {
        // code here
        if(!root) return -1;
        if(root->data==p || root->data==q || root->data==r) return root->data;
        int a = lca3Nodes(root->left,p,q,r);
        int b = lca3Nodes(root->right,p,q,r);
        if(a!=-1&&b!=-1) return root->data;
        return a==-1 ? b : a;
    }
};
```

