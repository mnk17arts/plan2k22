---
layout: post
title: Max Level Sum in Binary Tree
summary:
tags:
  - geeksforgeeks
  - array
  - bfs
  - queue
  - cpp
  - easy
minute: 8+ min
---

## Problem Statement - [_link_](https://practice.geeksforgeeks.org/problems/4b7ff87c26ed23b3f63c25c611690213d44fb6aa/1)

Given a Binary Tree having positive and negative nodes. Find the maximum sum of a level in the given Binary Tree.

**Your Task:**

You dont need to read input or print anything. Complete the function maxLevelSum() which takes root node as input parameter and returns the maximum sum of any horizontal level in the given Binary Tree

**Expected Time Complexity:** `O(N)`, where N is no of node.  
**Expected Auxiliary Space:** `O(W)`, Where W is the max width of the tree. 

### Examples

**Example 1:**

```
Input :               
             4
          /    \
         2     -5
        / \    / \
      -1   3  -2  6

Output: 6

Explanation :
Sum of all nodes of 0'th level is 4
Sum of all nodes of 1'th level is -3
Sum of all nodes of 2'th level is 6
Hence maximum sum is 6
```

**Example 2:**

```
Input :          
            1
          /   \
         2     3
        / \     \
       4   5     8
                / \
               6   7  

Output :  17

Explanation: Maximum sum is at level 2.
```

### Constraints

- `0 <= n <= 10^4`

## Solutions

```cpp

/* Tree node structure  used in the program
 struct Node
 {
     int data;
     Node* left, *right;
}; */

class Solution{
  public:
    /*You are required to complete below method */
    int maxLevelSum(Node* root) {
        // Your code here
        queue<Node*> q;
        q.push(root);
        int res = root->data;
        while(q.size()) {
            int n = q.size();
            int cur = 0;
            while(n--) {
                auto cur_node = q.front();
                q.pop();
                cur += cur_node->data;
                if(cur_node->left) {
                    q.push(cur_node->left);
                }
                if(cur_node->right) {
                    q.push(cur_node->right);
                }
            }
            res = max(res, cur);
        }
        return res;
    }
};

```
