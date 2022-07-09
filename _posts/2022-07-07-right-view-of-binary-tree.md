---
layout: post
title: Right View of Binary Tree         
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/right-view-of-binary-tree/0/?track=DSASP-Tree&batchId=154#)  

Given a Binary Tree, find Right view of it. Right view of a Binary Tree is set of nodes visible when tree is viewed from right side.

Right view of following tree is 1 3 7 8.

          1
       /     \
     2        3    
   /   \    /    \   
  4     5   6    7   
    \    
     8

**Your Task:** 
Just complete the function `rightView()` that takes node as parameter and returns the right view as a list.  

**Expected Time Complexity:** `O(N)`     
**Expected Auxiliary Space:** `O(h)` , where h = height of tree  

### Examples

**Example 1:**   
```
Input:
       1
    /    \
   3      2
Output: 1 2
```


**Example 2:**   
```
Input:
     10
    /   \
  20     30
 /   \
40  60 
Output: 10 30 60
```


### Constraints

+ `1 <= Number of nodes <= 10^5`
+ `1 <= Data of a node <= 10^5`

## Solutions

```cpp
class Solution {
  public:
    //Function to return list containing elements of right view of binary tree.
    vector<int> rightView(Node *root)
    {
        vector<int> res;
        if (root == NULL)
            return res;
        queue<Node *> q;
        q.push(root);
        
        while (!q.empty())
        {
            int size = q.size();
            for (int i = 0; i < size; i++)
            {
                Node *temp = q.front();
                if(i==size-1) res.push_back(temp->data);
                q.pop();
                if (temp->left)
                    q.push(temp->left);
                if (temp->right)
                    q.push(temp->right);
            }
        }
        return res;
    }
};
```

