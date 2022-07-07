---
layout: post
title: Mirror Tree        
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - easy
minute: 4 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/mirror-tree/0/?t)  

Given a Binary Tree, convert it into its mirror.   
<img src="https://contribute.geeksforgeeks.org/wp-content/uploads/mirrortrees.jpg">

**Your Task:** 
Just complete the function `mirror()` that takes node as paramter  and convert it into its mirror. The printing is done by the driver code only.

**Expected Time Complexity:** `O(N)`   
**Expected Auxiliary Space:** `O(h)` where `h` is height of the tree.

### Examples

**Example 1:**   
```
Input:
      10
     /  \
    20   30
   /  \
  40  60
Output: 30 10 60 20 40
Explanation: The tree is
      10               10
    /    \  (mirror) /    \
   20    30    =>   30    20
  /  \                   /   \
 40  60                 60   40
The inroder traversal of mirror is
30 10 60 20 40.
```

**Example 2:**   
```
Input:
      1
    /  \
   2    3
Output: 3 1 2
Explanation: The tree is
   1    (mirror)  1
 /  \    =>      /  \
2    3          3    2
The inorder of mirror is 3 1 2
```


### Constraints

+ `1 <= Number of nodes <= 10^5`
+ `0 <= Data of a node <= 10^5`

## Solutions

```cpp
class Solution {
  public:
    Node* nitish(Node* root){
        if(!root) return NULL;
        if(!root->left && !root->right) return root;
        Node* pleft = nitish(root->left);
        Node* pright = nitish(root->right);
        root->left = pright;
        root->right = pleft;
        return root;
    }
    // Function to convert a binary tree into its mirror tree.
    void mirror(Node* node) {
        // code here
        if(!node) return;
        nitish(node);
    }
};
```

