---
layout: post
title: Vertical Traversal of Binary Tree              
summary:
tags:
    - tree
    - bst
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/print-a-binary-tree-in-vertical-order/0/?track=DSASP-BST&batchId=154#)  

Given a Binary Tree, find the vertical traversal of it starting from the leftmost level to the rightmost level.
If there are multiple nodes passing through a vertical line, then they should be printed as they appear in level order traversal of the tree.


**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `verticalOrder()` which takes the root node as input parameter and returns an array containing the vertical order traversal of the tree from the leftmost to the rightmost level. If 2 nodes lie in the same vertical level, they should be printed in the order they appear in the level order traversal of the tree 


**Expected Time Complexity:** `O(N)`      
**Expected Auxiliary Space:** `O(N)`  

### Examples

**Example 1:**   
```
Input:
           1
         /   \
       2       3
     /   \   /   \
   4      5 6      7
              \      \
               8      9           
Output: 
4 2 1 5 6 3 8 7 9 
Explanation:
```   
<img src="https://media.geeksforgeeks.org/img-practice/ScreenShot2021-05-28at3-1622541589.png">

**Example 2:**   
```
Input:
       1
    /    \
   2       3
 /    \      \
4      5      6
Output: 4 2 1 5 3 6
```


### Constraints

+ `1 <= Number of nodes <= 3*10^4`

## Solutions

```cpp
class  Solution
{
    public:
    //Function to find the vertical order traversal of Binary Tree.
    vector<int> verticalOrder(Node *root)
    {
        //Your code here
        vector<int> v;
        queue<pair<Node*,int>> q;
        map<int,vector<int>> m;
        q.push({root,0});
        while(!q.empty()){
           Node* n = q.front().first;
           int d = q.front().second;
           q.pop();
           if(n->left) q.push({n->left,d-1});
           if(n->right) q.push({n->right,d+1});
           m[d].push_back(n->data);
        }
        for(auto i: m)
            for(auto j: i.second)
                v.push_back(j);
        return v;
    }
};
```

