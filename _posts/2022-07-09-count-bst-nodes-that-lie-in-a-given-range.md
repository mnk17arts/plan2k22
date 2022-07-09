---
layout: post
title: Count BST nodes that lie in a given range            
summary:
tags:
    - tree
    - bst
    - geeksforgeeks
    - cpp
    - medium
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/count-bst-nodes-that-lie-in-a-given-range/0/?track=DSASP-BST&batchId=154)  

Given a Binary Search Tree (BST) and a range l-h(inclusive), count the number of nodes in the BST that lie in the given range.

+ The values smaller than root go to the left side
+ The values greater and equal to the root go to the right side


**Your Task:** 
This is a function problem. You don't have to take input. You are required to complete the function `getCountOfNode()` that takes `root, l ,h` as parameters and returns the count. 

**Expected Time Complexity:** `O(N)`      
**Expected Auxiliary Space:** `O(h)`  

### Examples

**Example 1:**   
```
Input:
     5
    /  \
   4    6
  /      \
 3        7
l = 2, h = 8
Output: 5
Explanation: All the nodes are in the
given range.
```   

**Example 2:**   
```
Input:
      10
     /  \
    5    50
   /    /  \
  1    40  100
l = 5, h = 45
Output: 3
Explanation: 5 10 40 are the node in the
range
```


### Constraints

+ `1 <= Number of nodes <= 100`
+ `1<= l < h < 10^3`

## Solutions

```cpp
//Function to count number of nodes in BST that lie in the given range.
class Solution{
public:

    int getCount(Node *root, int l, int h)
    {
      // your code goes here  
      if(!root) return 0;
      int res = 0;
      if(root->left) res += getCount(root->left,l,h);
      if(l <= root->data && root->data <= h) res++;
      if(root->right) res += getCount(root->right,l,h);
      return res;
    }
};
```

