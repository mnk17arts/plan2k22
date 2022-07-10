---
layout: post
title:  Minimum BST Sum Subtree            
summary:
tags:
    - tree
    - bst
    - geeksforgeeks
    - cpp
    - hard
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/contest/challenge-6-tree-bst/problems/)  

Given a binary tree and a target, find the length of minimum subtree with the given sum equal to target which is also a binary search tree.


**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `minSubtreeSumBST()` which takes root and target as its input and returns length of largest subtree having sum equal to target which is also a BST.



### Examples

**Example 1:**   
```
Input:
           13
         /    \
       5       23
      / \      / \
     N   17   N   N
         /
        16
Target: 38
Output: 3
Explanation: 5,17,16 is the smallest subtree
with length 3.
```


**Example 2:**   
```
Input:
             7
           /   \
          N    23
             /   \
            10    23
           /  \   / \
          N   17 N   N
Target: 73
Output: -1
Explanation: No subtree is bst for the given target.
```


### Constraints

+ `1 <= N <= 10^5`

## Solutions

```cpp
class Solution
{
    public:
    bool isBST(Node* root, int i=INT_MIN, int x=INT_MAX){
        return root&& root->data < x && root->data > i &&
            isBST(root->left,i,root->data) &&
            isBST(root->right,root->data,x) || !root;
    }
    pair<int, int> helper(Node* root, int x, int &res){
        if(!root) return {0,0};
        if(!root->left&&!root->right) {
            if(root->data==x) res = 1;
            return {root->data,1};
        }
        auto l = helper(root->left,x,res);
        auto r = helper(root->right,x,res);
        int sum = l.first + r.first + root->data;
        int len = l.second + r.second + 1;
        if(sum==x) if(isBST(root)) res = res==-1 ? len : min(res,len);
        return {sum,len};
    }
    int minSubtreeSumBST(int target, Node *root) {
        // code here
        int res = -1;
        helper(root,target,res);
        return res;
    }
};
```

