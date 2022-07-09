---
layout: post
title: Floor in BST             
summary:
tags:
    - tree
    - bst
    - geeksforgeeks
    - cpp
    - medium
minute: 7 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/implementing-floor-in-bst/0/?track=DSASP-BST&batchId=154)  

Given a Binary search tree and a value X,  the task is to complete the function which will return the floor of x.

Note: Floor(X) is an element that is either equal to X or immediately smaller to X. If no such element exits return -1.


**Your Task:** 
You don't need to worry about the insert function, just complete the function `floor()` which should return the floor of `X`. If no such element exits return `-1`. 


**Expected Time Complexity:** `O(h)`      
**Expected Auxiliary Space:** `O(h)`  

### Examples

**Example 1:**   
```
Input:
       3
     /   \
    2     5
        /  \
       4    7
      /
     3
X = 1
Output: -1
Explanation: No smaller element exits
```


**Example 2:**   
```
Input:
       8
     /  \
    5    9
   / \    \
  2   6   10
X = 3
Output: 2
Explanation: Floor of 3 in the given BST
is 2
```


### Constraints

+ `1 <= Number of nodes <= 10^5`
+ `1 <= X, Value of Node <= 10^6`

## Solutions

```cpp
// Function to return the floor of given number in BST.
int floor(Node* root, int key) {
    // Your code goes here
    if(!root) return -1;
    if(root->data==key) return key;
    else if(root->data > key) return floor(root->left,key);
    int temp = floor(root->right,key);
    if(root->data > temp) return root->data;
    else return temp;
}
```

