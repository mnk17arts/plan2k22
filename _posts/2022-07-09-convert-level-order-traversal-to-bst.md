---
layout: post
title: Convert Level Order Traversal to BST            
summary:
tags:
    - tree
    - bst
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/convert-level-order-traversal-to-bst/0/?track=DSASP-BST&batchId=154)  

Given an array of size `N` containing level order traversal of a BST. The task is to complete the function `constructBst()`, that construct the BST (Binary Search Tree) from its given level order traversal


**Your Task:** 
Your task is to complete the function `constructBst()` which has two arguments, first as the array containing level order traversal of BST and next argument as the length of array which return the root of the newly constructed BST. The preorder traversal of the tree is printed by the driver's code. 

**Expected Time Complexity:** `O(N)`      
**Expected Auxiliary Space:** `O(N)`  

### Examples

**Example 1:**   
```
Input:
N = 6
BST[] = {1,3,4,6,7,8}
Output: 1 3 4 6 7 8
Explanation: After constructing BST, the
preorder traversal of BST is 1 3 4 6 7 8.
```   

**Example 2:**   
```
Input:
N = 9
BST[] = {7,4,12,3,6,8,1,5,10}
Output: 7 4 3 1 6 5 12 8 10
Explanation: After constructing BST, the
preorder traversal of BST is
7 4 3 1 6 5 12 8 10.
```


### Constraints

+ `1 <= Number of nodes <= 10^3`
+ `1 <= data <= 10^5`

## Solutions

```cpp
//Function to construct the BST from its given level order traversal.
Node* constructBst(int arr[], int n)
{
    // Code here
    Node* root = NULL;
    if(!n) return root;
    
    queue<pair<Node*,pair<int,int>>> q;
    root = new Node(arr[0]);
    q.push({root, {INT_MIN,INT_MAX}});
    int i=1;
    while(!q.empty()&&i<n){
        Node* node = q.front().first;
        int s=q.front().second.first;
        int e=q.front().second.second;
        q.pop();
        if(s < arr[i] && arr[i] < node->data){
            node->left = new Node(arr[i++]);
            q.push({node->left,{s,node->data}});
        }
        // else node->left = NULL;
        if(node->data < arr[i] && arr[i] < e){
            node->right = new Node(arr[i++]);
            q.push({node->right,{node->data,e}});
        }
    }
    return root;
}
```

