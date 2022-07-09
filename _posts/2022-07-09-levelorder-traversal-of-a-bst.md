---
layout: post
title: Levelorder traversal of a BST           
summary:
tags:
    - tree
    - bst
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/levelorder-traversal-of-a-bst/0/?track=DSASP-BST&batchId=154#)  

Levelorder traversal means traversing through the tree level by level, from left to right.
Given a BST, find its level-order traversal. 


**Your Task:** 
You don't need to read input or print anything. Complete the function `levelOrder()` that takes the root of the BST as input parameter and returns a list of integers containing the level-order traversal of the BST.

**Expected Time Complexity:** `O(N)`      
**Expected Auxiliary Space:** `O(N)`  

### Examples

**Example 1:**   
```
Input:
    30
   /
 10
   \ 
   20
Output: 30 10 20
```


**Example 2:**   
```
Input:
      5
    /   \
   2     7
   \      \
    3      8
Output: 5 2 7 3 8

```


### Constraints

+ `1 <= Number of nodes <= 10^5`
+ `1 <= Data of a node <= 10^5`

## Solutions

```cpp
// Function to return the level order traversal of a BST.
vector<int> levelOrder(struct Node* node) {
    // code here
    vector<int> v;
    queue<Node*> q;
    q.push(node);
    while (!q.empty()) {
        Node *p = q.front();
        q.pop();
        v.push_back(p->data);
        if (p->left != NULL)
            q.push(p->left);
        if (p->right != NULL)
            q.push(p->right);
    }
    return v;
    
}
```

