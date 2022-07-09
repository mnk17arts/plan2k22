---
layout: post
title: Bottom View of Binary Tree           
summary:
tags:
    - tree
    - bst
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/bottom-view-of-binary-tree/0/?track=DSASP-BST&batchId=154#)  

Given a binary tree, print the bottom view from left to right.
A node is included in bottom view if it can be seen when we look at the tree from bottom.

                      20
                    /    \
                  8       22
                /   \        \
              5      3       25
                    /   \      
                  10    14

For the above tree, the bottom view is 5 10 3 14 25.
If there are multiple bottom-most nodes for a horizontal distance from root, then print the later one in level traversal. For example, in the below diagram, 3 and 4 are both the bottommost nodes at horizontal distance 0, we need to print 4.

                      20
                    /    \
                  8       22
                /   \     /   \
              5      3 4     25
                     /    \      
                 10       14

For the above tree the output should be 5 10 4 14 25.


**Your Task:** 
This is a functional problem, you don't need to care about input, just complete the function `bottomView()` which takes the root node of the tree as input and returns an array containing the bottom view of the given tree.

**Expected Time Complexity:** `O(N)`      
**Expected Auxiliary Space:** `O(N)`  

### Examples

**Example 1:**   
```
Input:
       1
     /   \
    3     2
Output: 3 1 2
Explanation:
First case represents a tree with 3 nodes
and 2 edges where root is 1, left child of
1 is 3 and right child of 1 is 2.
```   
<img src="https://contribute.geeksforgeeks.org/wp-content/uploads/BT-1.jpg">      

```
Thus nodes of the binary tree will be
printed as such 3 1 2.
```



**Example 2:**   
```
Input:
         10
       /    \
      20    30
     /  \
    40   60
Output: 40 20 60 30

```


### Constraints

+ `1 <= Number of nodes <= 10^5`
+ `1 <= data <= 10^5`

## Solutions

```cpp
class Solution
{
    public:
    vector <int> bottomView(Node *root) {
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
            m[d] = p->data;
        }
        vector<int> res;
        for (auto it : m)
            res.push_back(it.second);
        return res;
    }

};
```

