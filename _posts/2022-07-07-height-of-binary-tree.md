---
layout: post
title: Height of Binary Tree        
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/height-of-binary-tree/0#)  

Given a binary tree, find its height.

**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `height()` which takes root node of the tree as input parameter and returns an integer denoting the height of the tree. If the tree is empty, return `0`. 

**Expected Time Complexity:** `O(N)` 
**Expected Auxiliary Space:** `O(N)`

### Examples

**Example 1:**   
```
Input:
     1
    /  \
   2    3
Output: 2
```

**Example 2:**   
```
Input:
  2
   \
    1
   /
 3
Output: 3   
```


### Constraints

+ `1 <= Number of nodes <= 10^5`
+ `0 <= Data of a node <= 10^5`

## Solutions

```cpp
class Solution{
    public:
    //Function to find the height of a binary tree.
    int height(struct Node* node){
        // code here 
        if(!node) return 0;
        return 1+max(height(node->left), height(node->right));
    }
};
```

