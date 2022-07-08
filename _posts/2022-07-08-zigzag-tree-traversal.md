---
layout: post
title: ZigZag Tree Traversal           
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - easy
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/zigzag-tree-traversal/0/?track=DSASP-Tree&batchId=154#)  

Given a Binary Tree. Find the Zig-Zag Level Order Traversal of the Binary Tree.

**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `zigZagTraversal()` which takes the root node of the Binary Tree as its input and returns a list containing the node values as they appear in the Zig-Zag Level-Order Traversal of the Tree.

**Expected Time Complexity:** `O(N)`      
**Expected Auxiliary Space:** `O(h)`  

### Examples

**Example 1:**   
```
Input:
        3
      /   \
     2     1
Output:
3 1 2
```


**Example 2:**   
```
Input:
           7
        /     \
       9       7
     /  \     /   
    8    8   6     
   /  \
  10   9 
Output:
7 7 9 8 8 6 9 10 
```


### Constraints

+ `1 <= Number of nodes <= 10^4`

## Solutions

```cpp
class Solution {
  public:
    //Function to store the zig zag order traversal of tree in a list.
    vector <int> zigZagTraversal(Node* root)
    {
    	// Code here
    	stack<Node*> s1,s2;
    	vector<int> res;
    	s1.push(root);
    	while(!s1.empty()||!s2.empty()){
    	    while(!s1.empty()){
    	        Node* temp = s1.top(); s1.pop();
    	        res.push_back(temp->data);
    	        if(temp->left) s2.push(temp->left);
    	        if(temp->right) s2.push(temp->right);
    	    }
    	    while(!s2.empty()){
    	        Node* temp = s2.top(); s2.pop();
    	        res.push_back(temp->data);
    	        if(temp->right) s1.push(temp->right);
    	        if(temp->left) s1.push(temp->left);
    	    }
    	}
    	return res;
    }
};
```

