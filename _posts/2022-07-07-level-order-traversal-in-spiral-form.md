---
layout: post
title: Level order traversal in spiral form         
summary:
tags:
    - tree
    - geeksforgeeks
    - cpp
    - easy
minute: 6 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/level-order-traversal-in-spiral-form/0/?track=DSASP-Tree&batchId=154)  

Complete the function to find spiral order traversal of a tree. For below tree, function should return `1, 2, 3, 4, 5, 6, 7.`

<img src="https://contribute.geeksforgeeks.org/wp-content/uploads/level.jpg">



**Your Task:** 
The task is to complete the function `findSpiral()` which takes root node as input parameter and returns the elements in spiral form of level order traversal as a list. The newline is automatically appended by the driver code.

**Expected Time Complexity:** `O(N)`      
**Expected Auxiliary Space:** `O(N)`  

### Examples

**Example 1:**   
```
Input:
           10
         /     \
        20     30
      /    \
    40     60
Output: 10 20 30 60 40 
```


**Example 2:**   
```
Input:
      1
    /   \
   3     2
Output:1 3 2
```


### Constraints

+ `0 <= Number of nodes <= 10^5`
+ `0 <= Data of a node <= 10^5`

## Solutions

```cpp
//Function to return a list containing the level order traversal in spiral form.
vector<int> findSpiral(Node *root)
{
    //Your code here
    vector<int> res;
    if (root == NULL)
        return res;
    stack<Node *> s1, s2;
    s2.push(root);
    while (!s1.empty() || !s2.empty()) {
        while (!s1.empty()) {
            Node *temp = s1.top();
            res.push_back(temp->data);
            s1.pop();
            if (temp->left)
                s2.push(temp->left);
            if (temp->right)
                s2.push(temp->right);
        }
        while (!s2.empty()) {
            Node *temp = s2.top();
            res.push_back(temp->data);
            s2.pop();
            if (temp->right)
                s1.push(temp->right);
            if (temp->left)
                s1.push(temp->left);
        }
    }
    return res;
}

```

