---
layout: post
title: Construct Binary Tree from Parent Array           
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - medium
minute: 8 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/construct-binary-tree-from-parent-array/0/?track=DSASP-Tree&batchId=154#)  

Given an array of size `N` that can be used to represents a tree. The array indexes are values in tree nodes and array values give the parent node of that particular index (or node). The value of the root node index would always be `-1` as there is no parent for root. Construct the standard linked representation of Binary Tree from this array representation.

**Note**: If two elements have the same parent, the one that appears first in the array will be the left child and the other is the right child. 


**Your Task:** 
You don't need to read input or print anything. The task is to complete the function `createTree()` which takes `2` arguments `parent[]` and `N` and returns the root node of the constructed tree.

**Expected Time Complexity:** `O(N)`      
**Expected Auxiliary Space:** `O(N)`  

### Examples

**Example 1:**   
```
Input:
N = 3
parent[] = {2, 0, -1}
Output: 2 0 1
Explanation: the tree generated will
have a sturcture like
               2
             /   
            0      
          /   
         1    
```


**Example 2:**   
```
Input:
N = 7
parent[] = {-1,0,0,1,1,3,5}
Output: 0 1 2 3 4 5 6
Explanation: the tree generated
will have a structure like 
          0
        /   \
       1     2
      / \
     3   4
    /
   5
 /
6
```


### Constraints

+ `1 <= Number of nodes <= 10^3`

## Solutions

```cpp
class Solution
{
    public:
    //Function to construct binary tree from parent array.
    Node *createTree(int parent[], int N)
    {
        // Your code here
        Node* tree[N];
        for(int i=0; i<N; i++) tree[i] = new Node(i);
        Node* root;
        for(int i=0; i<N; i++) {
            if(parent[i]==-1) root=tree[i];
            else if(!tree[parent[i]]->left) tree[parent[i]]->left=tree[i];
            else tree[parent[i]]->right=tree[i];
        }
        return root;
    }
};
```

