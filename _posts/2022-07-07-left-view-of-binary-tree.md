---
layout: post
title: Left View of Binary Tree          
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - easy
minute: 5 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/left-view-of-binary-tree/0/?)  

Given a Binary Tree, print Left view of it. Left view of a Binary Tree is set of nodes visible when tree is visited from Left side. The task is to complete the function `leftView()`, which accepts root of the tree as argument.

Left view of following tree is 1 2 4 8.
```
          1
       /     \
     2        3
   /   \    /    \
  4     5   6    7
   \
     8    
```


**Your Task:** 
You just have to complete the function `leftView()` that returns an array containing the nodes that are in the left view. The newline is automatically appended by the driver code.  

**Expected Time Complexity:** `O(N)`      
**Expected Auxiliary Space:** `O(N)`   

### Examples

**Example 1:**   
```
Input:
   1
 /  \
3    2
Output: 1 3
```


**Example 2:**   
```
Input:
```

<img src="https://media.geeksforgeeks.org/wp-content/cdn-uploads/20190221103723/leftview.jpg">

``` 
Output: 10 20 40
```


### Constraints

+ `0 <= Number of nodes <= 100`
+ `1 <= Data of a node <= 10^3`

## Solutions

```cpp
//Function to return a list containing elements of left view of the binary tree.
vector<int> leftView(Node *root)
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
            if(i==0) res.push_back(temp->data);
            q.pop();
            if (temp->left)
                q.push(temp->left);
            if (temp->right)
                q.push(temp->right);
        }
    }
    return res;
}
```

