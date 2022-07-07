---
layout: post
title: Maximum Width of Tree          
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/maximum-width-of-tree/0/?)  

Given a Binary Tree, find the maximum width of it. Maximum width is defined as the maximum number of nodes in any level.
For example, maximum width of following tree is 4 as there are 4 nodes at 3rd level.

```
          1
       /    \
     2       3
   /   \    /  \
  4    5   6    7
    \
      8 
```


**Your Task:** 
You don't have to read any input. Just complete the function getMaxWidth() that takes node as parameter and returns the maximum width. The printing is done by the driver code.

**Expected Time Complexity:** `O(N)`      
**Expected Auxiliary Space:** `O(N)`  

### Examples

**Example 1:**   
```
Input:
       1
     /    \
    2      3
Output: 2
```


**Example 2:**   
```
Input:
        10
      /     \
    20      30
   /    \
  40    60
Output: 2
```


### Constraints

+ `1 <= Number of nodes <= 10^5`
+ `0 <= Data of a node <= 10^5`

## Solutions

```cpp
class Solution{
    public:
    // Function to get the maximum width of a binary tree.
    int getMaxWidth(Node* root) {
    
        if (root == NULL)
            return 0;
        queue<Node *> q;
        q.push(root);
        int maxWidth = 0;
        while (!q.empty())
        {
            int size = q.size();
            maxWidth = max(maxWidth, size);
            for (int i = 0; i < size; i++)
            {
                Node *temp = q.front();
                q.pop();
                if (temp->left)
                    q.push(temp->left);
                if (temp->right)
                    q.push(temp->right);
            }
        }
        return maxWidth;
    }
};
```

