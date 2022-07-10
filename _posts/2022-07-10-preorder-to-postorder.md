---
layout: post
title: Preorder to Postorder           
summary:
tags:
    - tree
    - bst
    - stack
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/preorder-to-postorder4423/0/?track=DSASP-BST&batchId=154#)  

Given an array `arr[]` of `N` nodes representing preorder traversal of BST. The task is to print its postorder traversal.
In Pre-Order traversal, the root node is visited before the left child and right child nodes.
Post-order traversal is one of the multiple methods to traverse a tree.


**Your Task:** 
You need to complete the given function and return the root of the tree. The driver code will then use this root to print the post order traversal.

**Expected Time Complexity:** `O(N)`      
**Expected Auxiliary Space:** `O(N)`  

### Examples

**Example 1:**   
```
Input:
N = 5
arr[]  = {40,30,35,80,100}
Output: 35 30 100 80 40
Explanation: PreOrder: 40 30 35 80 100
InOrder: 30 35 40 80 100
Therefore, the BST will be:
              40
           /      \
         30       80
           \        \   
           35      100
Hence, the postOrder traversal will
be: 35 30 100 80 40
```


**Example 2:**   
```
Input:
N = 8
arr[]  = {40,30,32,35,80,90,100,120}
Output: 35 32 30 120 100 90 80 40
```


### Constraints

+ `1 <= N <= 10^3`
+ `1 <= data <= 10^4`

## Solutions

```cpp
class Solution
{
    public:
    //Function that constructs BST from its preorder traversal.
    Node* post_order(int pre[], int size)
    {
        //code here
        Node* root = NULL;
        if(!size) return root;
        root = newNode(pre[0]);
        int i=1;
        stack<Node*> s;
        Node* temp = root;
        
        while(i<size){
            if(pre[i] < temp->data){
                temp->left = newNode(pre[i++]);
                s.push(temp);
                temp = temp->left;
            }
            else {
                if(s.empty() || (pre[i] < s.top()->data)){
                    temp->right = newNode(pre[i++]);
                    temp = temp->right;
                }else {
                    temp = s.top(); s.pop();
                }
            }
        }
        return root;
    }
};
```

