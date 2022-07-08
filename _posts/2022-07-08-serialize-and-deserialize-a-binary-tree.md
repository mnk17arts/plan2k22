---
layout: post
title: Serialize and Deserialize a Binary Tree           
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - medium
minute: 9 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/serialize-and-deserialize-a-binary-tree/0/?t)  

Serialization is to store a tree in an array so that it can be later restored and Deserialization is reading tree back from the array. Now your task is to complete the function serialize which stores the tree into an array `A[ ]` and deSerialize which deserializes the array to the tree and returns it.
**Note**: The structure of the tree must be maintained. Multiple nodes can have the same data.

**Your Task:** 
The task is to complete two functions serialize which takes the root node of the tree as input and stores the tree into an array and deSerialize which deserializes the array to the original tree and returns the root of it.

**Expected Time Complexity:** `O(N)`      
**Expected Auxiliary Space:** `O(N)`  

### Examples

**Example 1:**   
```
Input:
      1
    /   \
   2     3
Output: 2 1 3
```


**Example 2:**   
```
Input:
         10
       /    \
      20    30
    /   \
   40  60
Output: 40 20 60 10 30
```


### Constraints

+ `1 <= Number of nodes <= 10^3`
+ `1 <= Node value <= 10^3`

## Solutions

```cpp
class Solution {
  public:
    void nitish(Node* root, vector<int> &res){
        if(!root) {res.push_back(-1);return;}
        res.push_back(root->data);
        nitish(root->left, res);
        nitish(root->right, res);
    }
    //Function to serialize a tree and return a list containing nodes of tree.
    vector<int> serialize(Node *root) 
    {
        //Your code here
        vector<int> res;
        nitish(root, res);
        return res;
        
    }
    
    //Function to deserialize a list and construct the tree.
    int i=0;
    Node * deSerialize(vector<int> &A)
    {
       //Your code here
        if(i>=A.size() || A[i]==-1) {i++; return NULL;}
        Node* root = new Node(A[i++]);
        root->left = deSerialize(A);
        root->right = deSerialize(A);
        return root;
       
    }
};
```

