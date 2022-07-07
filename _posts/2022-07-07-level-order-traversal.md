---
layout: post
title: Level order traversal          
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - easy
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/level-order-traversal/0/?)  

Given a binary tree, find its level order traversal.
Level order traversal of a tree is breadth-first traversal for the tree.



**Your Task:** 
You don't have to take any input. Complete the function `levelOrder()` that takes the root node as input parameter and returns a list of integers containing the level order traversal of the given Binary Tree.

**Expected Time Complexity:** `O(N)`      
**Expected Auxiliary Space:** `O(N)`  

### Examples

**Example 1:**   
```
Input:
    1
  /   \ 
 3     2
Output:1 3 2
```


**Example 2:**   
```
Input:
        10
     /      \
    20       30
  /   \
 40   60
Output:10 20 30 40 60
```


### Constraints

+ `1 <= Number of nodes <= 10^5`
+ `1 <= Data of a node <= 10^5`

## Solutions

```cpp
class Solution
{
    public:
    //Function to return the level order traversal of a tree.
    vector<int> levelOrder(Node* root)
    {
      //Your code here
        if (root == NULL)
            return {};
        queue<Node *> q;
        q.push(root);
        vector<int> res;
        while (!q.empty())
        {
            Node *temp = q.front();
            res.push_back(temp->data);
            q.pop();
            if (temp->left)
                q.push(temp->left);
            if (temp->right)
                q.push(temp->right);
        }
        return res;
    }
};
```

