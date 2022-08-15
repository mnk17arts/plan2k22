---
layout: post
title: Number of Turns in Binary Tree                       
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - hard
minute: 10+ min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/number-of-turns-in-binary-tree/1)  

Given a binary tree and data value of two of its nodes. Find the number of turns needed to reach from one node to another in the given binary tree. 

**Your Task:** 

You don't need to read input or print anything. Complete the function NumberOFTurns() which takes root node and data value of 2 nodes as input parameters and returns the number of turns required to navigate between them. If the two nodes are in a straight line, ie- the path does not involve any turns, return -1.


**Expected Time Complexity:** `O(N)`                
**Expected Auxiliary Space:** `O(height of the tree)`


### Examples

**Example 1:**   
```
Input:      
Tree = 
           1
        /    \
       2       3
     /  \     /  \
    4    5   6    7                        
   /        / \                        
  8        9   10   
first node = 5
second node = 10
Output: 4
Explanation: 
Turns will be at 2, 1, 3, 6.
```

**Example 2:**   
```
Input:      
Tree = 
           1
        /     \
       2        3
     /  \      /  \
    4    5    6    7                        
   /         / \                        
  8         9   10   
first node = 1
second node = 4  
Output: -1
Explanation: No turn is required since 
they are in a straight line.
```

### Constraints

+ `1 <= N <= 10^3`


## Solutions

```cpp
/*
Structure of the node of the tree is as follows 
struct Node {
    struct Node* left, *right;
    int data;
};
*/

class Solution{
  public:
    int ans = 0;
    Node* lca(Node* root, int f, int s){
        if(root==NULL) return root;
        if(root->data==f || root->data==s ) return root;
        Node* ln = lca(root->left,f,s);
        Node* rn = lca(root->right,f,s);
        if(ln&&rn) return root;
        return ln?ln:rn;
    }
    int notUtil(Node* root,Node* lcan, int f, int s, int t){
        if(root==NULL) return -1;
        if((root->data==f || root->data==s) && root!=lcan){
            return t;
        }
        int l = notUtil(root->left,lcan,f,s,0);
        int r = notUtil(root->right,lcan,f,s,1);
        if(l!=-1&&r!=-1){
            return ++ans;
        }
        if(l!=-1 && t!=-1){
            if(l!=t) ans++;
        }else if(r!=-1 && t!=-1) {
            if(r!=t) ans++;
        }
        return (l!=-1||r!=-1) ? t : -1;
        
    }
    // function should return the number of turns required to go from first node to second node 
    int NumberOFTurns(struct Node* root, int first, int second)
    {
      // Your code goes here
      if(!root->left&&!root->right) return -1;
      Node* lcan = lca(root,first,second);
      int _ = notUtil(lcan,lcan,first,second,-1);
      return ans!=0 ? ans : -1 ;
      
    }
};
```

