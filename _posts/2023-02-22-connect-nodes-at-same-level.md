---
layout: post
title: Connect Nodes at Same Level
summary:
tags:
  - geeksforgeeks
  - tree
  - cpp
  - medium
minute: 10+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/95423710beef46bd66f8dbb48c510b2c320dab05/1)

Given a binary tree, connect the nodes that are at the same level. The structure of the tree Node contains an addition nextRight pointer for this purpose.

Initially, all the nextRight pointers point to garbage values. Your function should set these pointers to point next right for each node.

**Your Task:**

You don't have to read input or print anything. Complete the function connect() that takes the root of the tree as  input parameter and connects the nodes that lie at the same level. 

Note: The generated output will contain 2 lines. First line contains the level order traversal of the tree and second line contains the inorder traversal of the tree.


**Expected Time Complexity:** `O(N)`  
**Expected Auxiliary Space:** `O(N)` 

### Examples

**Example 1:**

```
Input:
     3
   /  \
  1    2
Output:
3 1 2
1 3 2
Explanation:The connected tree is
       3 ------> NULL
     /   \
    1---> 2 -----> NULL
```

**Example 2:**

```
Input:
      10
    /   \
   20   30
  /  \
 40  60
Output:
10 20 30 40 60
40 20 60 10 30
Explanation:The connected tree is
        10 ---> NULL
       /   \
     20---> 30 ---> NULL
   /   \
 40---> 60 ---> NULL
```

### Constraints

- `1 ≤ Number of nodes ≤ 10^5`
- `0 ≤ Data of a node ≤ 10^5`

## Solutions

```cpp

/* struct Node {
    int data;
    Node* left;
    Node* right;
    Node* nextRight;
};*/

class Solution{
    public:
    void connect(Node *root)
    {
       // Code Here
       if(!root) return;
       queue<Node*> q;
       q.push(root);
       while(q.size()){
           int n = q.size();
           Node* temp = NULL;
           for(int i = 0; i < n; i++) {
               auto cur = q.front();
               q.pop();
               cur->nextRight = temp;
               if(cur->right) {
                   q.push(cur->right);
               } 
               if(cur->left) {
                   q.push(cur->left);
               }
               temp = cur;
           }
       }
    }    
};

```
