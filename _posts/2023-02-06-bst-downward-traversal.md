---
layout: post
title: BST Downward Traversal
summary:
tags:
    - geeksforgeeks
    - bst
    - cpp
    - easy
minute: 10+ min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/c85e3a573a7de6dfd18398def16d05387852b319/1) 

Given a Binary Search Tree and a target value. You have to find the node whose data is equal to target and return the sum of all descendant node's data which are vertically below the target node. Initially you are at the root node.

Note: If target node is not present in bst then return -1.

**Your Task:** 

You don't need to read input or print anything. Your task is to complete the function verticallyDownBST() which takes BST(you are given root node of bst ) and target as input, and return an interger value as the sum of vertically down nodes from target. If target is not present in bst then return -1.



**Expected Time Complexity:** `O(N)` where N is the number of nodes in the BST.              
**Expected Auxiliary Space:** `O(H)` where H is the height of the tree 



### Examples

**Example 1:**   
```
Input:
```
<img src="https://media.geeksforgeeks.org/img-practice/BSTDownwardTraversal-1662975635.png">

```
Target = 35
Output: 32
Explanation: Vertically below 35 is 32.
```

**Example 2:** 
```
Input:
```
<img src="https://media.geeksforgeeks.org/img-practice/BSTDownwardTraversal-1662975635.png">  

```
Target = 25
Output: 52
Explanation: Vertically below 25 is 22, 30 and their sum is 52.
```

### Constraints

+ `1 <= n < 10^6`
+ `1 <= target <= n`
+ `1 <= Node's data <= 10^6`

## Solutions

```cpp

/*
struct Node {
    int data;
    Node *left;
    Node *right;

    Node(int val) {
        data = val;
        left = right = NULL;
    }
};
*/

class Solution{
    public:
    long long int res = 0;
    void solve(Node *root, int x=0) {
        if(!root) return;
        if(x == 0) {
            res += root->data;
        }
        solve(root->left, x-1);
        solve(root->right, x+1);
    }
    long long int verticallyDownBST(Node *root,int target){
        // Code here
        if(!root) return -1;
        if(root->data == target) {
            solve(root);
            return res-(root->data);
        }
        if(root->data > target) {
            return verticallyDownBST(root->left, target);
        } 
        else {
            return verticallyDownBST(root->right, target);
        }
    }
};

```
