---
layout: post
title: Top View of Binary Tree           
summary:
tags:
    - tree
    - bst
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/top-view-of-binary-tree/0/?track=DSASP-BST&batchId=154)  

Given below is a binary tree. The task is to print the top view of binary tree. Top view of a binary tree is the set of nodes visible when the tree is viewed from the top. For the given below tree

```
      1    
    /   \    
   2     3    
  /  \  /  \    
 4   5  6   7    
```

Top view will be: 4 2 1 3 7
Note: Return nodes from leftmost node to rightmost node.


**Your Task:** 
Since this is a function problem. You don't have to take input. Just complete the function `topView()` that takes root node as parameter and returns a list of nodes visible from the top view from left to right.

**Expected Time Complexity:** `O(N)`      
**Expected Auxiliary Space:** `O(N)`  

### Examples

**Example 1:**   
```
Input:
       10
    /      \
  20        30
 /   \    /    \
40   60  90    100
Output: 40 20 10 30 100
```


**Example 2:**   
```
Input:
      1
   /    \
  2      3
Output: 2 1 3

```


### Constraints

+ `1 <= Number of nodes <= 10^5`
+ `1 <= data <= 10^5`

## Solutions

```cpp
class Solution
{
    public:
    //Function to return a list of nodes visible from the top view 
    //from left to right in Binary Tree.
    vector<int> topView(Node *root)
    {
        //Your code here
        if (root == NULL)
            return {};
        map<int, int> m;
        queue<pair<Node *, int>> q;
        q.push({root, 0});
        while (!q.empty()) {
            Node *p = q.front().first;
            int d = q.front().second;
            q.pop();
            if (p->left != NULL)
                q.push({p->left, d-1});
            if (p->right != NULL)
                q.push({p->right, d+1});
            if(m.find(d) == m.end())
                m[d] = p->data;
        }
        vector<int> res;
        for (auto it : m)
            res.push_back(it.second);
        return res;
    }

};
```

