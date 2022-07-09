---
layout: post
title: Print BST elements in given range             
summary:
tags:
    - tree
    - bst
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/print-bst-elements-in-given-range/0/?track=DSASP-BST&batchId=154)  

Given a Binary Search Tree and a range `[low, high]`. Find all the numbers in the BST that lie in the given range.
**Note:** Element greater than or equal to root go to the right side.


**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `printNearNodes()` which takes the root Node of the BST and the range elements low and high as inputs and returns an array that contains the BST elements in the given range low to high (inclusive) in non-decreasing order. 


**Expected Time Complexity:** `O(N)`      
**Expected Auxiliary Space:** `O(h)`  

### Examples

**Example 1:**   
```
Input:
       16
     /    \
    7     20
  /   \
 1    10
l = 13, h = 23
Output: 16 20 
```


**Example 2:**   
```
Input:
       17
     /    \
    4     18
  /   \
 2     9 
l = 4, h = 24
Output: 4 9 17 18 
```


### Constraints

+ `1 <= Number of nodes <= 10^4`
+ `1 <= l <= h <= 10^5`

## Solutions

```cpp
class Solution {
  public:
    vector<int> printNearNodes(Node *root, int low, int high) {
        //code here  
        vector<int> res ;
        if(!root) return res;
        vector<int> l = printNearNodes(root->left,low,high);
        res.insert(res.end(),l.begin(),l.end());
        if(low <= root->data && root->data <= high) res.push_back(root->data);
        vector<int> r = printNearNodes(root->right,low,high);
        res.insert(res.end(),r.begin(),r.end());
        return res;
    }
};
```

