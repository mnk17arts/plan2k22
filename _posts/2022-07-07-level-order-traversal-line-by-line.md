---
layout: post
title: Level order traversal Line by Line          
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - easy
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/level-order-traversal-line-by-line/0/)  

Given a Binary Tree, your task is to find its level order traversal.
For the below tree the output will be `1 $ 2 3 $ 4 5 6 7 $ 8 $`.


```
          1
       /     \
     2        3
   /    \     /   \
  4     5   6    7
    \
     8
```



**Your Task:** 
This is a function problem. You don't need to read input. Just complete the function `levelOrder()` that takes nodes as parameter and returns level order traversal as a 2D list.

Note: The driver code prints the levels '`$`' separated.

**Expected Time Complexity:** `O(N)`      
**Expected Auxiliary Space:** `O(N)`  

### Examples

**Example 1:**   
```
Input:
            10
          /    \
        20      30
     /     \
    40     60
Output: 10 $ 20 30 $ 40 60 $
```


**Example 2:**   
```
Input:
          1
        /
       4
     /   \
    4     2
Output:1 $ 4 $ 4 2 $
```


### Constraints

+ `1 <= Number of nodes <= 10^3`
+ `0 <= Data of a node <= 100`

## Solutions

```cpp
//Function to return the level order traversal line by line of a tree.
vector<vector<int>> levelOrder(Node* root)
{   vector<vector<int>> res;
    if (root == NULL)
        return res;
    queue<Node *> q;
    q.push(root);
    
    while (!q.empty())
    {
        int size = q.size();
        vector<int> line;
        for (int i = 0; i < size; i++)
        {
            Node *temp = q.front();
            line.push_back(temp->data);
            q.pop();
            if (temp->left)
                q.push(temp->left);
            if (temp->right)
                q.push(temp->right);
        }
        res.push_back(line);
    }
    return res;
}

```

